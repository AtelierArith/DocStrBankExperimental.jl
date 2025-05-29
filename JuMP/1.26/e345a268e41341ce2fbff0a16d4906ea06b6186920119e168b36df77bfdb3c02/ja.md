```
flatten!(expr::GenericNonlinearExpr)
```

非線形式をインプレースでフラット化し、ネストされた `+` および `*` ノードを単一の n-ary 操作に持ち上げます。

## 動機

演算子オーバーロードを使用して作成された非線形式は、深くネストされており、バランスが取れていない場合があります。たとえば、`prod(x for i in 1:4)` は `*(x, *(x, *(x, x)))` を生成し、より好ましい `*(x, x, x, x)` ではありません。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> y = prod(x for i in 1:4)
((x²) * x) * x

julia> flatten!(y)
(x²) * x * x

julia> flatten!(sin(prod(x for i in 1:4)))
sin((x²) * x * x)
```
