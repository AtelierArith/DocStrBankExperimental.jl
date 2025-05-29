```
Imputer(
   Dict(
      # 補完戦略。
      # ベクトルを取る統計量、例えば平均または中央値。
      :strategy => mean
   )
)
```

Float64特徴からNaN値を補完します。

`fit!`と`transform`を実装しています。
