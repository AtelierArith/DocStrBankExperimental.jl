```
RandomVariable{T}
```

RandomVariableは異なるモデルパラメータに「割り当てる」ことができます。その値は直接使用することも、指定されたパラメータの参照値に加えたり、乗算したりすることで適用することもできます。分布はインスタンス化されている必要があることに注意してください。例えば、RandomVariable(:foo, Normal())のように呼び出す必要があり、RandomVariable(:foo, Normal)のようには呼び出せません。
