```
 @NLparameters(model, args...)
```

モデル `model` に複数の非線形パラメータを作成して返します。これは [`@NLparameter`](@ref) マクロと同様の方法です。

モデルは最初の引数でなければならず、複数のパラメータは `begin ... end` ブロック内で複数行にわたって追加できます。異なるパラメータは、以下の例のように別々の行に配置する必要があります。

このマクロは、定義されたパラメータを含むタプルを返します。

# 例

```jldoctest; setup=:(using JuMP)
model = Model()
@NLparameters(model, begin
    x == 10
    b == 156
end)
value(x)

# 出力
10.0
```

```

```
