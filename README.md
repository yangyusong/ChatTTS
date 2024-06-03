# ChatTTS

只是简单使用的话，看上面这段就够了，windows下可用，不用科学上网
-----------------------
使用流程

git clone https://github.com/yangyusong/ChatTTS.git

pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple

pip install modelscope -i https://pypi.tuna.tsinghua.edu.cn/simple
pip install gradio -i https://pypi.tuna.tsinghua.edu.cn/simple

python app.py

网页访问
http://127.0.0.1:7860/
----------------------------------

操作流程参考了文章：
[本地搭建ChatTTS WebUi](https://blog.csdn.net/weixin_53226786/article/details/139399756)

ChatTTS是专门为对话场景设计的文本转语音模型，例如LLM助手对话任务。它支持英文和中文两种语言。最大的模型使用了10万小时以上的中英文数据进行训练。在HuggingFace中开源的版本为4万小时训练且未SFT的版本.




[男说话人](https://github.com/2noise/ChatTTS/assets/130631963/bbfa3b83-2b67-4bb6-9315-64c992b63788)

[女说话人](https://github.com/2noise/ChatTTS/assets/130631963/e061f230-0e05-45e6-8e4e-0189f2d260c4)




---
## 常见问题

##### 连不上HuggingFace
请使用[modelscope](https://www.modelscope.cn/models/pzc163/chatTTS)的版本. 并设置cache的位置:
```python
chat.load_models(source='local', local_path='你的下载位置')
```

##### 我要多少显存? Infer的速度是怎么样的?
对于30s的音频, 至少需要4G的显存. 对于4090, 1s生成约7个字所对应的音频. RTF约0.3.

##### 模型稳定性似乎不够好, 会出现其他说话人或音质很差的现象.
这是自回归模型通常都会出现的问题. 说话人可能会在中间变化, 可能会采样到音质非常差的结果, 这通常难以避免. 可以多采样几次来找到合适的结果.

##### 除了笑声还能控制什么吗? 还能控制其他情感吗?
在现在放出的模型版本中, 只有[laugh]和[uv_break], [lbreak]作为字级别的控制单元. 在未来的版本中我们可能会开源其他情感控制的版本.

