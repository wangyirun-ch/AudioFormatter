Code=UTF-8 Language=简体中文
瑞安中学下课铃转码器 AudioFormatter
开发语言：Python    依赖：FFmpeg（AudioFormatter//Environment//ffmpeg.exe）
开发者：浙江省瑞安中学 2303 王乙润（Peppa Wang）
最新版本发行时间：2024年5月30日
开源许可证：MIT License

项目起源：2024年3月，下课铃《Cocopops》、《All My People》播放异常；2o24年4月，下课铃《Dar+ling》播放异常.具体体现为声音模糊、鼓点较轻。
经排查，发现在当前操作的转码流程中使的软件“格式工厂”异常转码。

原理分析：瑞安中学的广播系统所支持的音频参数为(128kbps,41000Hz,1ch,mp3)
然而，以上几首下课铃的参数为(128kbps,44100Hz,2ch,mp3)。双声道的音频总数据量不变，但有50%的数据是不可被播放的。因此，双声道音频的音质会低于单声道音频。(比特率=声道数*采样率*采样深度*压缩率)
另外，“将式工厂”的工作原理是使用ffmpeg进行转码，但会产生部分数据无法写入的情况，进而产生削波现象，产生鼓点较轻的问题。其根本原因在于转码后没有进行对音颜文件的校验

项目构造：
1、Input文件夹：文件输入文件夹
2、Output文件夹：文件输出文件夹
3、Temp文件夹：临时中继文件夹
4、Environment文件夹----ffmpeg.exe：依赖内核
5、AudioFormatter.exe：可执行文件
6、AudioFormatter.py：源代码文件
7、Parameters.txt：输出参数存档文件
8、Package.cmd：Pyinstaller打包命令行
9、License：MIT开源许可证
10、ICON.ico：可执行文件图标

使用方法：
1、运行AudioFormatter.exe，会出现一个命令行控制台；
2、为防止数据丢失，请确保“Input”与“Output”文件夹中无文件，并键入回车；
3、在打开的“Input”文件夹下放入待处理的音频文件；
4、按提示顺序输入下课铃的顺序编号；
5、在确认输出参数无误后，键入回车开始转码；
6、在打开的“Output”文件夹中取走处理完成的音频，处理结束。

版本更新：
Version1.0：2024年5月23日，完成基本功能架构；
Version1.1：2024年5月28日，添加Parameter.txt，方便后续参数的更改与维护；
Version1.2：2024年5月30日，集成FFmpeg，免安装直接使用；

联系开发者：
邮箱：wangyirun0111@163.com或2125664650@qq.com
QQ：2125664650    微信：WangYr_Peppa7590