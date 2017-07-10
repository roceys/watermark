#### 使用场景分类
* 文本水印
* **图像水印**  (当前目标)
* 音频水印
* 视频水印

#### 水印算法
* 空间域上，经典的 `LSB`（ Least Significant Bits）,支持的水印信息量大，对原图影响小。但是抗干扰能力比较差，不能抵抗图像的裁剪、缩放和jpg压缩。
* 频域上，不支持盲提取算法，例如：`DCT`，`DWT`，抗干扰能力强。但提取时需要原图。
* 频域上，支持盲提取算法，例如:`DWT+SVD`，主要是使用图像中的稳定特征作为作为提取的指引，一般使用图像矩阵的特征值。相比DWT，抗干扰能力差一些，可附加的水印信息量小一些
    * 提取时不需要水印图像，缺点是能嵌入的信息非常有限。
    * 提取时需要水印图像，优点是嵌入信息比较多，实现上是把水印的信息分成两部分。

> 综合我司的使用场景，建议使用第一种或者第三种方法。 

#### 运行
``` 
    python test.py
``` 

>所有代码由python实现，可封装成dll、so、web服务。

#### 名词解释：
* 盲嵌入：嵌入的水印信号与载体作品无关
* 盲提取：提取水印时不需要原图像
* 不可视水印：肉眼看不到的水印
* PSNR：顶峰信噪比，用来度量加了水印之后的图像好坏，数字越大越好，超过35，肉眼就很难看出区别。

#### 历史
* 1954年，出现了第一个与“数字水印”方法类似的技术实例。当时，美国Muzac公司的Emil Hembrooke申请了一项名为“Identification of Sond and Lide Singals”的专利。改专利描述了一种将标识码不可感知的嵌入到音乐中而证明所有权的方法。这是迄今为止所知道的最早的电子水印技术.
* 1993年Cox等提出了一种其余扩频通信思想的水印方案。该方案相对于空域算法具有较好的鲁棒性，已经成为数字水印技术中一个比较经典的方案。但它也存在一些缺陷，其中最重要的一点就是提取水印信息时必须有原始图像的参与
* Chen等于1998年提出了一类盲水印方案。该方案采用量化器来实现水印信息的嵌入，在容量和鲁棒性等方面都具有较好的性能，并已成为数字水印技术中一个比较典型的方案。
* 关于音频水印技术的研究最早见于1996年，Bender提出了LSB编码、回声编码、扩频编码和相位编码等四种算法
* 对文本水印的研究始于1994年，贝尔实验室的Maxemchuk首先提出在数字文档中嵌入标记的方法，用于保护电子出版物所有者的利益。
* 视频水印的研究也始于1994年，当时Matsui等提出了一种类似于图像水印的视频水印算法，它将视频信号的每一帧简单地视作图像进行处理

