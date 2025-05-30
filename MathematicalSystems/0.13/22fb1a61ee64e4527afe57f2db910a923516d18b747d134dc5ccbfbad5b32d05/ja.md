```
VaryingInput{UT, VUT<:AbstractVector{UT}} <: AbstractInput
```

時間とともに変化する可能性のある入力を表す型です。

### フィールド

  * `U` – 入力セットのベクトル

### 例

変化する入力はベクトルを保持し、その長さはベクトル内の要素の数に等しいです。例えば、有理数のベクトルによって与えられる入力を考えてみましょう：

```jldoctest varying_input
julia> v = VaryingInput([-1//2, 1//2])
VaryingInput{Rational{Int64}, Vector{Rational{Int64}}}(Rational{Int64}[-1//2, 1//2])

julia> length(v)
2

julia> eltype(v)
Rational{Int64}
```

Baseの`iterate`メソッドは入力と整数の状態を受け取り、入力要素と次の反復状態を返します：

```jldoctest varying_input
julia> iterate(v, 1)
(-1//2, 2)

julia> iterate(v, 2)
(1//2, 3)
```

`nextinput`メソッドは変化する入力と整数`n`を受け取り、この入力の最初の`n`要素に対するイテレータを返します（デフォルトでは`n=1`）：

```jldoctest varying_input
julia> typeof(nextinput(v))
Base.Iterators.Take{VaryingInput{Rational{Int64}, Vector{Rational{Int64}}}}

julia> collect(nextinput(v, 1))
1-element Vector{Rational{Int64}}:
 -1//2

julia> collect(nextinput(v, 2))
2-element Vector{Rational{Int64}}:
 -1//2
  1//2
```

入力を配列に収集することができ、同等にリスト内包表記を使用することもできます（または`for`ループを使用することもできます）：

```jldoctest varying_input
julia> collect(v)
2-element Vector{Rational{Int64}}:
 -1//2
  1//2

julia> [3*vi for vi in v]
2-element Vector{Rational{Int64}}:
 -3//2
  3//2
```

この入力型は有限であるため、長さよりも多くの要素を問い合わせると、全ベクトルが返されます：

```jldoctest varying_input
julia> collect(nextinput(v, 4))
2-element Vector{Rational{Int64}}:
 -1//2
  1//2
```

変化する入力を変換するには、次のように`map`を使用できます：

```jldoctest varying_input
julia> map(x->3*x, v)
VaryingInput{Rational{Int64}, Vector{Rational{Int64}}}(Rational{Int64}[-3//2, 3//2])
```
