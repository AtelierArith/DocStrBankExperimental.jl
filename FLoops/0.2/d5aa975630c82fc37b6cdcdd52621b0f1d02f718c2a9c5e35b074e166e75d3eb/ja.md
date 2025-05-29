```
@reduce() do (acc₁ [= init₁]; x₁), ..., (accₙ [= initₙ]; xₙ)
    ...
end
@reduce(acc₁ ⊗₁= x₁, ..., accₙ ⊗ₙ= xₙ)
@reduce(acc₁ .⊗₁= x₁, ..., accₙ .⊗ₙ= xₙ)
@reduce(acc₁ = ⊗₁(init₁, x₁), ..., accₙ = ⊗ₙ(initₙ, xₙ))
@reduce(acc₁ .= (⊗₁).(init₁, x₁), ..., accₙ = (⊗ₙ).(initₙ, xₙ))
```

累積器が逐次的な基本ケースでどのように更新され、2つの基本ケースから得られた累積器がどのように結合されるかを宣言します。

引数 `accᵢ` と `xᵢ` は記号でなければなりませんが、最後の3つの形式の `xᵢ` では式を使用できます。

最初の形式では、

```julia
function ((acc₁, acc₂, ..., accₙ), (x₁, x₂, ..., xₙ))
    ...  # `do` ブロックの本体
    return (acc₁, acc₂, ..., accₙ)
end
```

は結合的な関数である必要があります。

最後の3つの形式では、すべての二項演算 `⊗ᵢ` は結合的な関数である必要があります。

`initᵢ` が指定されている場合、タプル `(init₁, init₂, ..., initₙ)` は関連する結合的な関数の単位元である必要があります。 `accᵢ = initᵢ` は各基本ケース（各 `Task`）の最初に評価されます。

次の形式のループを考えます。

```julia
@floop for ...
    # (x₁, x₂, ..., xₙ) を計算するコード
    @reduce() do (acc₁ = init₁; x₁), ..., (accₙ = initₙ; xₙ)
        # (x₁, x₂, ..., xₙ) を使用して (acc₁, acc₂, ..., accₙ) を更新するコード
    end
end
```

これは次のように変換されます。

```julia
acc₁ = init₁
...
accₙ = initₙ
for ...
    # (x₁, x₂, ..., xₙ) を計算するコード
    # (x₁, x₂, ..., xₙ) を使用して (acc₁, acc₂, ..., accₙ) を更新するコード
end
```

これは各基本ケースの `(acc₁, acc₂, ..., accₙ)` を計算するためです。 2つの基本ケースの累積器 `accᵢ` は、「(x₁, x₂, ..., xₙ) を使用して (acc₁, acc₂, ..., accₙ) を更新するコード」を使用して結合されます。ここで、`(x₁, x₂, ..., xₙ)` は次の基本ケースの `(acc₁, acc₂, ..., accₙ)` に置き換えられます。「(x₁, x₂, ..., xₙ) を計算するコード」は基本ケースを結合するためには使用されないことに注意してください。

# 例

```julia
@reduce() do (vmax=-Inf; v), (imax=0; i)
    if isless(vmax, v)
        vmax = v
        imax = i
    end
end

@reduce(s += y, p *= y)

@reduce(xs = append!!(EmptyVector(), x), ys = append!!(EmptyVector(), y))
```
