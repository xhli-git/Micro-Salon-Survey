# 从文本识别到智能文档解析的技术演进——“文档图像微沙龙”系列活动前沿综述


## 简介
文档图像分析与识别（Document Image Analysis and Recognition, DIAR）作为连接物理世界与数字信息的关键桥梁，其技术体系正经历从传统任务驱动向大模型时代智能理解的深刻变革。本文基于中国图象图形学学会文档图像分析与识别专业委员会主办的“文档图像微沙龙”系列学术活动，系统梳理并凝练了近年来中国青年学者在该领域的代表性成果。文章以技术演进为脉络，首先回顾了文字检测、识别、公式与表格等核心基础任务的创新突破，重点阐述了开放集识别、自监督学习等前沿范式；进而探讨了从独立任务到端到端联合优化的系统性进展；最后，聚焦于大模型时代下智能文档解析的新范式，深入剖析了专用光学字符识别（Optical Character Recognition, OCR）大模型、多模态文档解析框架以及评估体系构建等关键方向。本文旨在勾勒DIAR领域从精细化单点技术到智能化系统集成、再到认知级语义理解的发展全景，为构建高鲁棒性、可解释且高效的通用文档智能基座提供理论参考与实践指引。


## 本文覆盖工作列表
### 表1 OCR基础任务相关工作列表
<table border="1" class="ocr-table">
  <thead>
    <tr>
      <th>任务</th>
      <th>工作</th>
      <th>论文标题</th>
      <th>核心方法</th>
      <th>实验结果</th>
      <th>主要贡献</th>
      <th>文章链接</th>
      <th>开源链接</th>
    </tr>
  </thead>
  <tbody>
    <!-- 文字识别 -->
    <tr>
      <td rowspan="11" align="center"><strong>文字识别</strong></td>
      <td>OSTR (Liu等，2022)</td>
      <td>Towards open-set text recognition via label-to-prototype learning</td>
      <td>提出标签到原型学习框架，含ProtoCNN、开放集预测器和TPTNet</td>
      <td>模型无需重训练即可识别新字符，并能发现新字符</td>
      <td>首次形式化开放集文字识别任务，解决新字符泛化问题</td>
      <td><a href="https://www.sciencedirect.com/science/article/pii/S0031320322005891">文章</a></td>
      <td><a href="https://github.com/lancercat/OSOCR">代码</a></td>
    </tr>
    <tr>
      <td>CCD (Liu等，2023)</td>
      <td>Open-Set Text Recognition via Character-Context Decoupling</td>
      <td>通过DTA模块和DCA机制分离时序与语言上下文信息</td>
      <td>在日文假名等新字符识别上显著优于基线，缓解上下文偏置</td>
      <td>揭示并解决了上下文导致新字符被错误纠正的偏置问题</td>
      <td><a href="https://ieeexplore.ieee.org/document/9878508">文章</a></td>
      <td><a href="https://github.com/lancercat/VSDF">代码</a></td>
    </tr>
    <tr>
      <td>DiG (Yang等，2022)</td>
      <td>Reading and writing: Discriminative and generative modeling for self-supervised text recognition</td>
      <td>融合对比学习（CL）与掩码图像建模（MIM），共享ViT编码器</td>
      <td>在11个基准平均超越SOTA 5.3%，不规则文本提升10.2%-20.2%</td>
      <td>首次在文字识别中引入生成式自监督目标，提升通用表征能力</td>
      <td><a href="https://dl.acm.org/doi/10.1145/3503161.3547784">文章</a></td>
      <td><a href="https://github.com/ayumiymk/DiG">代码</a></td>
    </tr>
    <tr>
      <td>CCDPlus (Guan等，2025)</td>
      <td>Ccdplus: Towards accurate character to character distillation for text recognition</td>
      <td>构建联合监督与自监督学习（JSSL）框架，引入WCS模块和字符级蒸馏</td>
      <td>在Union14M-L上提升达6.1%</td>
      <td>统一框架弥合合成与真实数据域间隙，解决表征粗糙等问题</td>
      <td><a href="https://ieeexplore.ieee.org/document/10887029">文章</a></td>
      <td><a href="https://github.com/TongkunGuan/CCD">代码</a></td>
    </tr>
    <tr>
      <td>SemiETS (Luo等，2025)</td>
      <td>SemiETS: Integrating Spatial and Content Consistencies for Semi-Supervised End-to-end Text Spotting</td>
      <td>基于师生架构，提出PSA筛选可靠伪标签和MMS增强监督信号</td>
      <td>在0.5%标注比例下超越全监督基线，展现强域适应能力</td>
      <td>系统解决半监督端到端文字识别中伪标签质量差的核心挑战</td>
      <td><a href="https://openaccess.thecvf.com/content/CVPR2025/html/Luo_SemiETS_Integrating_Spatial_and_Content_Consistencies_for_Semi-Supervised_End-to-end_Text_CVPR_2025_paper.html">文章</a></td>
      <td><a href="https://github.com/DrLuo/SemiETS">代码</a></td>
    </tr>
    <tr>
      <td>SVTR (Du等，2022)</td>
      <td>Svtr: Scene text recognition with a single visual model</td>
      <td>单一视觉模型，交替局部/全局混合块提取多粒度特征</td>
      <td>英文达SOTA，中文最高+9.6%，推理更快</td>
      <td>摒弃传统混合架构，证明单一视觉模型可高效完成识别</td>
      <td><a href="https://www.ijcai.org/proceedings/2022/0124.pdf">文章</a></td>
      <td><a href="https://github.com/PaddlePaddle/PaddleOCR">代码</a></td>
    </tr>
    <tr>
      <td>CPPD (Du等，2025a)</td>
      <td>Context perception parallel decoder for scene text recognition</td>
      <td>并行解码器中引入字符计数（CC）和字符排序（CO）模块</td>
      <td>达SOTA精度，推理速度比自回归快约8倍</td>
      <td>解决并行解码精度低问题，在单次前向重建上下文引导能力</td>
      <td><a href="https://ieeexplore.ieee.org/document/10902187">文章</a></td>
      <td><a href="https://github.com/PaddlePaddle/PaddleOCR/blob/dygraph/doc/doc_en/algorithm_rec_cppd_en.md">代码</a></td>
    </tr>
    <tr>
      <td>IGTR (Du等，2025b)</td>
      <td>Instruction-guided scene text recognition</td>
      <td>将识别重构为指令学习，预测字符属性，使用三元组指令集</td>
      <td>超越SOTA，模型小（24.1M）、快（4-10ms），擅长稀有/形近字符</td>
      <td>提出指令引导新范式，通过属性预测深化文本理解</td>
      <td><a href="https://ieeexplore.ieee.org/document/10820836">文章</a></td>
      <td><a href="https://github.com/Topdu/OpenOCR">代码</a></td>
    </tr>
    <tr>
      <td>ViSu (Qu等，2024)</td>
      <td>Boosting semi-supervised scene text recognition via viewing and summarizing</td>
      <td>在Mean-Teacher中引入在线生成策略和对比损失</td>
      <td>能泛化到严重形变字符和艺术字</td>
      <td>提升半监督场景下对复杂字符的鲁棒性和性能上限</td>
      <td><a href="https://ieeexplore.ieee.org/document/9329114">文章</a></td>
      <td><a href="https://github.com/qqqyd/ViSu">代码</a></td>
    </tr>
    <tr>
      <td>统一字符分割与识别 (Yu等，2024)</td>
      <td>An approach for handwritten Chinese text recognition unifying character segmentation and recognition</td>
      <td>建模为滑动窗口候选分类与回归，联合显式/弱监督训练</td>
      <td>ICDAR-2013上CR 98.13%，F1 95.10%，0.1%标注下效果仍优</td>
      <td>无需真实字符级标注实现高精度分割与识别，提升可解释性</td>
      <td><a href="https://www.sciencedirect.com/science/article/pii/S0031320324001249">文章</a></td>
      <td>--</td>
    </tr>
    <tr>
      <td>多源上下文字符级置信度估计 (Liu等，2024b)</td>
      <td>Context-aware confidence estimation for rejection in handwritten chinese text recognition</td>
      <td>融合形状、语义、几何（BiBG）上下文，基于贝叶斯校准</td>
      <td>RP99从25.27%降至13.66%，有语言模型时从11.47%降至6.82%</td>
      <td>提出高可靠性拒识方案，显著提升置信度校准效果</td>
      <td><a href="https://link.springer.com/chapter/10.1007/978-3-031-70533-5_9">文章</a></td>
      <td>--</td>
    </tr>
    <!-- 公式识别 -->
    <tr>
      <td rowspan="4" align="center"><strong>公式识别</strong></td>
      <td>G2G (Wu等，2021)</td>
      <td>Graph-to-graph: towards accurate and interpretable online handwritten mathematical expression recognition</td>
      <td>图到图学习，GNN-GNN架构，子图注意力机制</td>
      <td>CROHME 2014/2016 ExpRate达54.46%/52.05%</td>
      <td>首次显式建模公式层次结构并实现符号分割</td>
      <td><a href="https://ojs.aaai.org/index.php/AAAI/article/view/16399">文章</a></td>
      <td>--</td>
    </tr>
    <tr>
      <td>SSD (Wu等，2022)</td>
      <td>Structural string decoder for handwritten mathematical expression recognition</td>
      <td>结构化字符串解码器，用占位符展平LaTeX，带记忆队列注意力</td>
      <td>CROHME 2014 ExpRate达53.1%</td>
      <td>平衡字符串与树解码器优缺点，显式建模层次结构</td>
      <td><a href="https://ieeexplore.ieee.org/document/9956105">文章</a></td>
      <td>--</td>
    </tr>
    <tr>
      <td>VLPG (Guo等，2025a)</td>
      <td>Vision-language pre-training for graph-based handwritten mathematical expression recognition</td>
      <td>视觉-语言预训练，定位与语言建模pretext任务，两步微调</td>
      <td>CROHME各年ExpRate提升至60%+，OffRaSHME达67.75%</td>
      <td>利用未配对数据缓解标注稀缺，提升泛化能力</td>
      <td><a href="https://www.sciencedirect.com/science/article/pii/S0031320325000068">文章</a></td>
      <td><a href="https://github.com/guohy17/VLPG">代码</a></td>
    </tr>
    <tr>
      <td>HiE-VL (Guo等，2025b)</td>
      <td>HiE-VL: A large vision-language model with hierarchical adapter for handwritten mathematical expression recognition</td>
      <td>分层大模型，SAM视觉编码器，“原始/结构”双适配器</td>
      <td>CROHME 2014 ExpRate达73.3%，远超GPT-4V和SOTA专用模型</td>
      <td>首个专为HMER设计的LVLM，证明其在复杂公式识别领先潜力</td>
      <td><a href="https://www.semanticscholar.org/paper/HiE-VL%3A-A-Large-Vision-Language-Model-with-Adapter-Guo-Yin/a89bfc2e1417b17d7da5e39442dce5a3fc496c92">文章</a></td>
      <td><a href="https://github.com/guohy17/HiE-VL">代码</a></td>
    </tr>
    <!-- 表格识别 -->
    <tr>
      <td rowspan="3" align="center"><strong>表格识别</strong></td>
      <td>WTW (Long等，2021)</td>
      <td>Parsing table structures in the wild</td>
      <td>CenterNet加循环配对模块，检测中心点与顶点，配对损失</td>
      <td>WTW上TEDS指标绝对优势24.6%，ICDAR2019达SOTA</td>
      <td>解决野外复杂表格单元格检测与分组难题</td>
      <td><a href="https://openaccess.thecvf.com/content/ICCV2021/papers/Long_Parsing_Table_Structures_in_the_Wild_ICCV_2021_paper.pdf">文章</a></td>
      <td><a href="https://github.com/wangwen-whu/WTW-Dataset">代码</a></td>
    </tr>
    <tr>
      <td>VAST (Huang等，2023)</td>
      <td>Improving table structure recognition with visual-alignment sequential coordinate modeling</td>
      <td>坐标序列解码器（自回归预测边界框）+视觉对齐损失</td>
      <td>六个基准上逻辑与物理结构指标均达SOTA</td>
      <td>解决生成式TSR物理结构预测不准问题，丰富局部视觉信息</td>
      <td><a href="https://openaccess.thecvf.com/content/CVPR2023/papers/Huang_Improving_Table_Structure_Recognition_With_Visual-Alignment_Sequential_Coordinate_Modeling_CVPR_2023_paper.pdf">文章</a></td>
      <td>--</td>
    </tr>
    <tr>
      <td>TabPedia (Zhao等，2024a)</td>
      <td>TabPedia: Towards comprehensive visual table understanding with concept synergy</td>
      <td>基于LVLM，概念协同机制，中介令牌融合多任务/多源嵌入</td>
      <td>多基准达SOTA或极具竞争力，支持端到端多轮对话解析</td>
      <td>统一VTU多任务，构建复杂理解新基准ComTQA</td>
      <td><a href="https://www.semanticscholar.org/paper/TabPedia:-Towards-Comprehensive-Visual-Table-with-Zhao-Feng/e7cb80f37c74aa3a1cbea138cc808e8ae02bb113">文章</a></td>
      <td><a href="https://github.com/zhaowc-ustc/TabPedia">代码</a></td>
    </tr>
    <!-- 版面分析 -->
    <tr>
      <td rowspan="3" align="center"><strong>版面分析</strong></td>
      <td>M6Doc (Cheng等，2023)</td>
      <td>M6doc: A large-scale multi-format, multi-type, multi-layout, multi-language, multi-annotation category dataset for modern document layout analysis</td>
      <td>发布“六多”特性真实世界文档数据集</td>
      <td>TransDLANet在M6Doc上达64.5% mAP</td>
      <td>填补中文及真实文档数据空白，推动细粒度布局分析</td>
      <td><a href="https://openaccess.thecvf.com/content/CVPR2023/papers/Cheng_M6Doc_A_Large-Scale_Multi-Format_Multi-Type_Multi-Layout_Multi-Language_Multi-Annotation_Category_Dataset_CVPR_2023_paper.pdf">文章</a></td>
      <td><a href="https://github.com/HCIILAB/M6Doc">代码</a></td>
    </tr>
    <tr>
      <td>DocLayout-YOLO (Zhao等，2024b)</td>
      <td>DocLayout-YOLO: Enhancing document layout analysis through diverse synthetic data and global-to-local adaptive perception</td>
      <td>布局合成（二维装箱）生成DocSynth-300K，GL-CRM多尺度模块</td>
      <td>DocStructBench上78.8% mAP，85.5 FPS</td>
      <td>解决预训练数据同质化，平衡效率与精度</td>
      <td><a href="https://arxiv.org/abs/2410.12628">文章</a></td>
      <td><a href="https://github.com/opendatalab/DocLayout-YOLO">代码</a></td>
    </tr>
    <tr>
      <td>DocSAM (Li等，2025a)</td>
      <td>DocSAM: Unified document image segmentation via query decomposition and heterogeneous mixed learning</td>
      <td>统一框架，Sentence-BERT语义查询+实例查询，开集分类</td>
      <td>在M6Doc等复杂基准上精度具竞争力，支持48数据集联合训练</td>
      <td>打破任务壁垒，证明单一模型处理多格式/语言/标注的强大泛化能力</td>
      <td><a href="https://openaccess.thecvf.com/content/CVPR2025/papers/Li_DocSAM_Unified_Document_Image_Segmentation_via_Query_Decomposition_and_Heterogeneous_CVPR_2025_paper.pdf">文章</a></td>
      <td><a href="https://github.com/xhli-git/DocSAM">代码</a></td>
    </tr>
    <!-- 端到端文本检测与识别 -->
    <tr>
      <td rowspan="2" align="center"><strong>端到端文本检测与识别</strong></td>
      <td>Text Perceptron (Qiao等，2020)</td>
      <td>Text Perceptron: Towards end-to-end arbitrary-shaped text spotting</td>
      <td>分割检测+STM/TPS形变校正，端到端微调控制点</td>
      <td>在Total-Text和SCUT-CTW1500显著领先</td>
      <td>融合检测与识别，实现不规则文本端到端优化</td>
      <td><a href="https://ojs.aaai.org/index.php/AAAI/article/view/6864">文章</a></td>
      <td>--</td>
    </tr>
    <tr>
      <td>MANGO (Qiao等，2021)</td>
      <td>MANGO: A mask attention guided one-stage scene text spotter</td>
      <td>单阶段，PMA模块直接从特征图读取字符，无RoI裁剪</td>
      <td>多基准达SOTA或竞争性能，推理更快</td>
      <td>支持任意形状文本识别，仅需粗定位即可端到端训练</td>
      <td><a href="https://ojs.aaai.org/index.php/AAAI/article/download/16348/16155">文章</a></td>
      <td>--</td>
    </tr>
  </tbody>
</table>

### 表2 文档解析相关工作列表
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>任务</th>
      <th>工作</th>
      <th>论文标题</th>
      <th>核心方法</th>
      <th>实验结果</th>
      <th>主要贡献</th>
      <th>文章链接</th>
      <th>开源链接</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="10"><strong>文档解析</strong></td>
      <td>GOT (Wei等，2024)</td>
      <td>General OCR theory: Towards OCR-2.0 via a unified end-to-end model</td>
      <td>580M统一编码器-解码器模型，三阶段训练，合成数据引擎</td>
      <td>多项任务达或超SOTA，可部署于消费级GPU</td>
      <td>提出通用OCR理论，实现所有人工光学信号的统一处理</td>
      <td><a href="https://arxiv.org/pdf/2409.01704.pdf">文章</a></td>
      <td><a href="https://github.com/opendatalab/MinerU">代码</a></td>
    </tr>
    <tr>
      <td>MinerU (Wang等，2024)</td>
      <td>MinerU: An open-source solution for precise document content extraction</td>
      <td>集成五个SOTA子模型，规则后处理解决布局问题</td>
      <td>11类文档高质量提取，公式识别媲美Mathpix</td>
      <td>证明精心设计的流水线在大模型时代仍有强大实用价值</td>
      <td><a href="https://arxiv.org/abs/2409.18839">文章</a></td>
      <td><a href="https://github.com/Ucas-HaoranWei/GOT-OCR2.0">代码</a></td>
    </tr>
    <tr>
      <td>PaddleOCR 3.0 (Cui等，2025a)</td>
      <td>PaddleOCR 3.0 technical report</td>
      <td>包含PP-OCRv5、PP-StructureV3、PP-ChatOCRv4三大方案</td>
      <td>PP-OCRv5超越十亿级VLM，PP-StructureV3在OmniDocBench达SOTA</td>
      <td>面向大模型时代需求，提供开源、高精度、多语言OCR工具包</td>
      <td><a href="https://arxiv.org/abs/2507.05595">文章</a></td>
      <td><a href="https://github.com/PaddlePaddle/PaddleOCR">代码</a></td>
    </tr>
    <tr>
      <td>PaddleOCR-VL (Cui等，2025b)</td>
      <td>PaddleOCR-VL: Boosting multilingual document parsing via a 0.9B ultra-compact vision-language model</td>
      <td>两阶段解耦架构（布局分析+并行识别），0.9B高效VLM</td>
      <td>多基准上超越GPT-4o等大模型，速度更快、资源消耗更低</td>
      <td>平衡端到端VLM与流水线优缺点，实现高效多语言文档解析</td>
      <td><a href="https://arxiv.org/abs/2510.14528">文章</a></td>
      <td><a href="https://github.com/PaddlePaddle/PaddleOCR">代码</a></td>
    </tr>
    <tr>
      <td>HunyuanOCR (Team等，2025)</td>
      <td>HunyuanOCR technical report</td>
      <td>1B端到端VLM，四阶段预训练+GRPO强化学习</td>
      <td>多基准超越更大开源模型及商业API，小模型赛道夺冠</td>
      <td>统一解决多样化OCR任务，兼顾效率与专业精度</td>
      <td><a href="https://arxiv.org/abs/2511.19575">文章</a></td>
      <td><a href="https://github.com/Tencent-Hunyuan/HunyuanOCR">代码</a></td>
    </tr>
    <tr>
      <td>DeepSeek-OCR (Wei等，2025a)</td>
      <td>DeepSeek-OCR: Contexts optical compression</td>
      <td>DeepEncoder视觉压缩（1024x1024→256 token）+MoE解码器</td>
      <td>100 token超越GOT-OCR2.0（256 token），&lt;800 token超越MinerU2.0</td>
      <td>将视觉作为高效压缩介质，缓解LLM长文本计算瓶颈</td>
      <td><a href="https://arxiv.org/abs/2510.18234">文章</a></td>
      <td><a href="http://github.com/deepseek-ai/DeepSeek-OCR">代码</a></td>
    </tr>
    <tr>
      <td>T-LLaVA (Wei等，2025b)</td>
      <td>T-LLaVA: An Effective Saliency-Aware Slicing Strategy for Text Recognition</td>
      <td>文本密度激活器+比率-分辨率自适应切片（RRS）+特征融合</td>
      <td>&lt;1B模型性能超越多个&gt;7B通用模型</td>
      <td>解决“分辨率-感知悖论”，兼顾文本细节与结构完整性</td>
      <td><a href="https://link.springer.com/chapter/10.1007/978-3-032-04614-7_20">文章</a></td>
      <td>--</td>
    </tr>
    <tr>
      <td>Dolphin (Feng等，2025)</td>
      <td>Dolphin: Document image parsing via heterogeneous anchor prompting</td>
      <td>“分析-再解析”范式：布局分析生成锚点，再并行解析内容</td>
      <td>元素级与页面级基准达SOTA，运行效率显著优于大模型</td>
      <td>兼顾精度、效率与布局结构完整性，避免错误传播与退化</td>
      <td><a href="https://arxiv.org/abs/2505.14059">文章</a></td>
      <td><a href="https://github.com/ByteDance/Dolphin">代码</a></td>
    </tr>
    <tr>
      <td>MonkeyOCR (Li等，2025b)</td>
      <td>MonkeyOCR: Document Parsing with a Structure-Recognition-Relation Triplet Paradigm</td>
      <td>SRR三元范式（结构-识别-关系），3B LMM并行识别</td>
      <td>OmniDocBench全面超越SOTA，优于72B模型，单卡高效部署</td>
      <td>精度与效率兼得，构建最全面双语文档数据集</td>
      <td><a href="https://arxiv.org/abs/2506.05218">文章</a></td>
      <td><a href="https://github.com/Yuliang-Liu/MonkeyOCR">代码</a></td>
    </tr>
    <tr>
      <td>MonkeyOCR v1.5 (Zhang等，2025b)</td>
      <td>MonkeyOCR v1.5 Technical Report: Unlocking Robust Document Parsing for Complex Patterns</td>
      <td>两阶段框架（联合布局/顺序预测+并行识别），IDTP/TGTM/RL优化</td>
      <td>OmniDocBench v1.5总体分92.9%，复杂子集领先8.2%</td>
      <td>显著提升复杂文档（多级表格、嵌入图像、跨页）鲁棒性</td>
      <td><a href="https://arxiv.org/abs/2511.10390">文章</a></td>
      <td><a href="https://github.com/Yuliang-Liu/MonkeyOCR">代码</a></td>
    </tr>
    <tr>
      <td rowspan="6"><strong>评测基准</strong></td>
      <td>OCRBench (Liu等，2024a)</td>
      <td>OCRBench: on the hidden mystery of ocr in large multimodal models</td>
      <td>覆盖5大任务、29数据集、1000问答对的系统性评估</td>
      <td>揭示LMM在手写/中文/HMER上平均差距超50%</td>
      <td>首个系统性LMM文本能力评估框架，揭示其依赖语义先验的短板</td>
      <td><a href="https://arxiv.org/pdf/2305.07895">文章</a></td>
      <td><a href="https://github.com/Yuliang-Liu/MultimodalOCR">代码</a></td>
    </tr>
    <tr>
      <td>OCRBench v2 (Fu等，2024)</td>
      <td>OCRBench v2: An improved benchmark for evaluating large multimodal models on visual text localization and reasoning</td>
      <td>扩展至31场景、23子任务、1万问答对，含私有测试集</td>
      <td>前沿模型总分普遍&lt;50，暴露五大核心局限</td>
      <td>通过高熵指令与私有集精准诊断LMM深层缺陷</td>
      <td><a href="https://arxiv.org/abs/2501.00321">文章</a></td>
      <td><a href="https://99franklin.github.io/ocrbench_v2">代码</a></td>
    </tr>
    <tr>
      <td>CDM (Wang等，2025)</td>
      <td>Image Over Text: Transforming Formula Recognition Evaluation with Character Detection Matching</td>
      <td>将LaTeX渲染为彩色图像，匈牙利匹配+RANSAC剔除无效匹配</td>
      <td>评分与人类偏好高度一致（96%）</td>
      <td>首创图像域公式评估，消除LaTeX风格差异带来的偏差</td>
      <td><a href="https://ieeexplore.ieee.org/document/11094480/citations#citations">文章</a></td>
      <td><a href="https://github.com/opendatalab/UniMERNet/tree/main/cdm">代码</a></td>
    </tr>
    <tr>
      <td>OmniDocBench (Ouyang等，2025)</td>
      <td>OmniDocBench: Benchmarking diverse PDF document parsing with comprehensive annotations</td>
      <td>覆盖9类文档、19布局、15属性，多层次评估体系</td>
      <td>揭示流水线与VLM各自优势场景</td>
      <td>构建全面真实文档基准，支持细粒度能力分析</td>
      <td><a href="https://ieeexplore.ieee.org/document/11091844">文章</a></td>
      <td><a href="https://github.com/opendatalab/OmniDocBench">代码</a></td>
    </tr>
    <tr>
      <td>OHRBench (Zhang等，2025a)</td>
      <td>OCR hinders RAG: Evaluating the cascading impact of OCR on retrieval-augmented generation</td>
      <td>定义语义/格式两类OCR噪声，评估其对RAG的级联损害</td>
      <td>最优OCR方案仍使RAG性能比真实数据低14%+</td>
      <td>首次量化OCR噪声对下游RAG系统的负面影响</td>
      <td><a href="https://openaccess.thecvf.com/content/ICCV2025/html/Zhang_OCR_Hinders_RAG_Evaluating_the_Cascading_Impact_of_OCR_on_ICCV_2025_paper.html">文章</a></td>
      <td><a href="https://github.com/opendatalab/OHR-Bench">代码</a></td>
    </tr>
    <tr>
      <td>TextHalu-Bench (Shu等，2025)</td>
      <td>When Semantics Mislead Vision: Mitigating Large Multimodal Models Hallucinations in Scene Text Spotting and Understanding</td>
      <td>构建幻觉基准，提出ZoomText+GLC无需训练的消除框架</td>
      <td>有效抑制LVLM在OCR任务中的语义幻觉</td>
      <td>首个专门针对OCR幻觉的基准与解决方案</td>
      <td><a href="https://arxiv.org/abs/2506.05551">文章</a></td>
      <td><a href="https://github.com/shuyansy/MLLM-Semantic-Hallucination">代码</a></td>
    </tr>
  </tbody>
</table>
