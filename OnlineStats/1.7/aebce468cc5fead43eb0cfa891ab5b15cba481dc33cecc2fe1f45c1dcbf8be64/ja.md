```
LinRegBuilder(p)
```

任意の変数を他の変数のセットに回帰させるオブジェクトを作成します。オプションで要素ごとのリッジ正則化を使用できます。`LinRegBuilder`で使用する主な関数は`coef`です：

```
coef(o::LinRegBuilder, λ = 0; y=1, x=[2,3,...], bias=true, verbose=false)
```

リッジ（`abs2`ペナルティ）パラメータ`λ`を使用して、列`y`を列`x`に回帰させた係数を返します。デフォルトで切片（`bias`）項が追加されます。

# 例

```
x = randn(1000, 10)
o = fit!(LinRegBuilder(), eachrow(x))

coef(o; y=3, verbose=true)

coef(o; y=7, x=[2,5,4])
```
