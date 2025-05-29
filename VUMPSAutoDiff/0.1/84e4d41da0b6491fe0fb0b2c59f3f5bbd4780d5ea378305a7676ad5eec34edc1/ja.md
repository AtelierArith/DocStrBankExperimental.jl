```
left_env(TM::AbstractLinearMap) -> AbstractTensorMap
```

転送行列の左環境テンソル (ρl) を計算するには、転送演算子の支配的な左固有ベクトルを見つけます。

# 引数

  * `TM`: 転送行列を表す抽象線形写像

# 戻り値

  * 左環境テンソル (左転送操作の不動点)
