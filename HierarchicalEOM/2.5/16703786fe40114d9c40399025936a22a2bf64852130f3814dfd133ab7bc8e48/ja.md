```
getADO(ados, idx)
```

特定のインデックスを持つ補助密度演算子を補助密度演算子から返します

この関数は、次の呼び出しと等しいです: `ados[idx]`。

# パラメータ

  * `ados::ADOs` : HEOMモデルのための補助密度演算子
  * `idx::Int` : 補助密度演算子のインデックス

# 戻り値

  * `ρ_idx::QuantumObject` : 補助密度演算子
