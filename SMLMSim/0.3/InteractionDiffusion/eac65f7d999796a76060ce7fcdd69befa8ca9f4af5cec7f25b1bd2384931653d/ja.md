```
get_dimers(smld::BasicSMLD)
```

ダイマー状態のエミッターのみを含む新しいBasicSMLDを抽出します。

# 引数

  * `smld::BasicSMLD`: すべてのエミッターを含む元のSMLD

# 戻り値

  * `BasicSMLD`: ダイマーのみを含む新しいSMLD

# 例

```julia
# シミュレーション結果からダイマーのみを抽出
smld = simulate(params)
dimer_smld = get_dimers(smld)
```
