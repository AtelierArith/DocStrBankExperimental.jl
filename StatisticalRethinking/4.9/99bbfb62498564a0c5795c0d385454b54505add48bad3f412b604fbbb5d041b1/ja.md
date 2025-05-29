# シミュレーション

反実仮想シミュレーションに使用されます。

```julia
simulate(df, coefs, var_seq)

```

### 必要な引数

```julia
* `df`                                 : 係数サンプルを含むDataFrame
* `coefs`                              : 係数のベクトル
* `var_seq`                            : シミュレーション効果のための入力値
```

### 戻り値

```julia
* `m_sim::NamedTuple`                  : 予測を含む配列
```
