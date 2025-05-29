# シミュレーション

変数を操作した後の反実仮想予測。

```julia
simulate(df, coefs, var_seq, coefs_ext)

```

### 必要な引数

```julia
* `df`                                 : コエフィシエントサンプルを含むDataFrame
* `coefs`                              : コエフィシエントのベクトル
* `var_seq`                            : シミュレーション効果のための入力値
* `ext_coefs`                          : シミュレーションされた変数コエフィシエントのベクトル
```

### 戻り値

```julia
* `(m_sim, d_sim)`                     : 予測を含む配列
```
