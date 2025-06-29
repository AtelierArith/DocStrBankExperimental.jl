```
identity_init([::AbstractRNG=Utils.default_rng()], [T=Float32], size...; gain::Number=1,
    shift::Union{Integer, Tuple{Integer, Integer}}=0) -> AbstractArray{T}
```

ニューラルネットワークのほとんどの層でパラメータとして使用した場合にアイデンティティマッピングを提供することを目的とした配列を構築します。アイデンティティマッピングは`gain`パラメータによってスケーリングされます。

# 挙動

  * 1D: ゼロの`Vector`を返します（`input_size == output_size`の場合のバイアスに便利です）。
  * 2D: アイデンティティ行列を返します（入力サイズと出力サイズが等しい全結合層に便利です）。
  * 2D以上: 最後の2次元に沿った中央スライスがアイデンティティ行列であり、残りはゼロのテンソルを返します（畳み込み層に便利で、アイデンティティ畳み込みをシミュレートします）。

# 注意点

  * この初期化子を使用しても、すべての層がアイデンティティマッピングを生成するわけではありません。例外には再帰層や正規化層が含まれます。
  * 完全なアイデンティティマッピングのためには、層は`input_size == output_size`でなければなりません。この条件が満たされない場合、関数は余分な次元をゼロでパディングします。
  * 畳み込み層がアイデンティティマッピングを達成するためには、カーネルサイズは奇数でなければならず、出力フィーチャーマップが入力フィーチャーマップと同じサイズになるように適切なパディングが適用される必要があります。

# 引数

  * `rng::AbstractRNG`: 他の初期化子との一貫性のために含まれるオプションの乱数生成器ですが、出力が決定論的であるため無視されます。
  * `T::Type{<:Number}`: 配列要素の数値型。
  * `size...`: 初期化される配列の次元。
  * `gain::Number=1`: アイデンティティマッピングに適用されるスケーリングファクター。
  * `shift::Union{Integer, Tuple{Integer, Integer}}=0`: 出力配列に適用される円形シフトを指定する整数またはタプル。

# 戻り値

  * `AbstractArray{T}`: アイデンティティマッピングを表すように初期化された配列で、`gain`によってスケーリングされ、オプションで`shift`によってシフトされます。

# 例

```jldoctest
julia> identity_init(Xoshiro(123), Float32, 5, 5)
5×5 Matrix{Float32}:
 1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0

julia> identity_init(Xoshiro(123), Float32, 3, 3, 1, 1; gain=1.5)
3×3×1×1 Array{Float32, 4}:
[:, :, 1, 1] =
 0.0  0.0  0.0
 0.0  1.5  0.0
 0.0  0.0  0.0
```
