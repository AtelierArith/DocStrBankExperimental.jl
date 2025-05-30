```
ConstantInput{UT} <: AbstractInput
```

時間的に一定の入力を表す型。

### フィールド

  * `U` – 入力セット

### 例

定数入力は単一の要素を保持し、その長さは無限です。フィールド `U` にアクセスするには、状態を与えてBaseの `iterate` を使用するか、希望する入力要素の数を与えて `nextinput` メソッドを使用します：

```jldoctest constant_input
julia> c = ConstantInput(-1//2)
ConstantInput{Rational{Int64}}(-1//2)

julia> iterate(c, 1)
(-1//2, nothing)

julia> iterate(c, 2)
(-1//2, nothing)

julia> collect(nextinput(c, 4))
4-element Vector{Rational{Int64}}:
 -1//2
 -1//2
 -1//2
 -1//2
```

この入力の要素は有理数です：

```jldoctest constant_input
julia> eltype(c)
Rational{Int64}
```

定数入力を変換するには、次のように `map` を使用できます：

```jldoctest constant_input
julia> map(x->2*x, c)
ConstantInput{Rational{Int64}}(-1//1)
```
