```
FixedPointDecimals.checked_rdiv(x::FD, y::FD) -> FD
```

`x / y` を計算し、適用可能な場合はオーバーフローエラーをチェックします。

オーバーフロープロテクションは、目に見えるパフォーマンスペナルティを課す可能性があります。

参照：

  * 切り捨て除算のための `Base.checked_div`。
