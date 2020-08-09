#SMP2020微博情绪分类评测
#三支小队安徽大学

1. 模型简介
所用模型为ROBERT+LSTM

2. 环境需求
python==3.7
numpy==1.14.5
tensorflow-gpu==1.13.1
keras==2.3.1

3. 数据集评测

   3.1 data文件简介
   为方便训练，将标签转为数字，对应关系如下
   0：happy
   1：angry
   2：sad
   3：fear
   4：surprise
   5：neural

   * data分为两个文件夹，usual为通用微博数据集文件夹，virus为疫情微博数据集文件夹\n
   * usual_train.txt    官方发布通用微博训练集\n
   * usual_test.txt    官方发布疫情微博数据集\n
   * train_sen.tsv    整理无标签训练集（每行一句）
   * test_sen.csv    整理无标签测试集（每行一句）
   * train_label.tsv    带标签训练集（每行标签+句子）
   * train.tsv    抽取2000条数据后的训练集（每行标签+句子）
   * dev.tsv    抽取2000条作为验证集（每行标签+句子）
   * train_emb.tsv    预训练得到的训练集句向量（每行768维向量）
   * test_emb.tsv    预训练得到的测试集句向量（每行768维向量）
   * virus文件夹与之对应

   3.2 评测主程序
   评测主程序为smp_main.py
   输入文件分别为usual和virus文件夹下的train_emb.tsv和test_emb.tsv
   输出文件为usual_result.txt和virus_result.txt
   运行命令为
   Python smp_main.py

4. 预训练句向量
以usual/train_sen.tsv为例

运行
sh RoBERT/train.sh
得到训练模型tmp/sim_model

运行
sh getemb.sh
得到句向量train_emb.tsv
