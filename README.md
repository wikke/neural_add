# Neural Add

> Add operation implemented by 2 layer stateful LSTM, with final accuracy 0.9771
> 
> 双层有状态LSTM循环神经网络实现加法运算，最终accuracy 0.9771

## Introduction

let's have an example: 70 + 38 = 108

Convert 2 inputs num to sequences in reverse order: `[0, 7, 0]`, `[8, 3, 0]`, and `[8, 0, 1]`

Since it's sequence, RNN(LSTM) would be a good choice. But how to handle `7+3=10`, there would be an increase in the higher bit. Yeah, stateful LSTM would help, since it take the last cell status as the input of the next RNN(LSTM) cell. But it's not enough, we need **2 layer stateful LSTM**, with the first layer return_sequences=True. The second RNN/LSTM layer handle the increment.

LSTM适用于数字序列情况，处理进位需要一个双层有状态LSTM，有状态LSTM可以把上一个Cell的状态作为下一个Cell的输入，双层中第二层是用于处理进位的情况。
