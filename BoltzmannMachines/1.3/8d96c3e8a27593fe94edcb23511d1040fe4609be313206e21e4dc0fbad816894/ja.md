```
updateparameters!(rbm, optimizer)
```

RBM `rbm` を更新します。これは、`optimizer` に対して `computegradient!` を呼び出すことで計算された勾配の方向に一歩進むことによって行われます。
