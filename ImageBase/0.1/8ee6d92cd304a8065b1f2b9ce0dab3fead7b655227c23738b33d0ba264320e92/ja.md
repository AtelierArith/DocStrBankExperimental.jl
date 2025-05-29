```
restrict(img[, dims]) -> imgr
```

`img`のサイズを、指定された`dims`に沿って約2倍縮小します。`dims`が指定されていない場合は、すべての空間座標が対象となります。

# 出力

出力配列`imgr`の型は、入力型に依存します：

  * `img`が`OffsetArray`の場合、出力配列`imgr`も`OffsetArray`になります。
  * `img`が`OffsetArray`でない場合、出力配列`imgr`はオフセットインデックスを持っていても`Array`型になります。

`imgr`のサイズは元のサイズの約`1/2`です。より具体的には：

  * `Nₖ = size(img, k)`が奇数の場合、`size(imgr, k) == (Nₖ+1) ÷ 2`。
  * `Nₖ = size(img, k)`が偶数の場合、`size(imgr, k) == (Nₖ÷2) + 1`。

# 例

オプションの引数`dims`は`Tuple`または`Integer`で指定できます：

```julia
A = rand(5, 5) # size: (5, 5)

restrict(A) # size: (3, 3)

restrict(A, 1) # size: (3, 5)
restrict(A, 2) # size: (5, 3)

restrict(A, (1, )) # size: (3, 5)
restrict(A, (1, 2)) # size: (3, 3)
```

入力配列が1ベースでない場合、原点は半分になります：

```julia
julia> using ImageBase, OffsetArrays

julia> Ao = OffsetArray(rand(5, 4), 5, 6);

julia> Ar = restrict(Ao);

julia> axes(Ao)
(OffsetArrays.IdOffsetRange(values=6:10, indices=6:10), OffsetArrays.IdOffsetRange(values=7:10, indices=7:10))

julia> axes(Ar)
(OffsetArrays.IdOffsetRange(values=3:5, indices=3:5), OffsetArrays.IdOffsetRange(values=4:6, indices=4:6))
```

# 拡張ヘルプ

`restrict`という用語は代数的多重格子法の粗化操作から取られています。これは「延長」（本質的には補間）の随伴です。`restrict`は画像を進行しながらアンチエイリアス処理を行うため、2x2ブロックの単純な合計よりも優れています。`restrict`の実装はパフォーマンスのために調整されており、[ピラミッド](https://en.wikipedia.org/wiki/Pyramid_(image_processing))を構築するための高速な方法であるべきです。

`l`が特定の次元に沿った`img`のサイズである場合、`restrict`は奇数の`l`に対してサイズ`(l+1)÷2`の配列を生成し、偶数の`l`に対しては`l÷2 + 1`の配列を生成します。以下の例を参照してください。

`ImageTransformations.imresize`も参照してください。

# 例

```julia
a_coarse = [0, 1, 0.3]
```

これを中間点で補間すると、次のようになります。

```julia
a_fine = [0, 0.5, 1, 0.65, 0.3]
```

`a_fine`は、次のように*延長*演算子`P`を介して`a_coarse`から得られます：`P*a_coarse`、ここで

```julia
P = [1   0   0;      # この行は最初の点を「コピー」します
     0.5 0.5 0;      # この行は最初と2番目の点の平均を取ります
     0   1   0;      # 2番目の点をコピーします
     0   0.5 0.5;    # 2番目と3番目の点の平均を取ります
     0   0   1]      # 3番目の点をコピーします
```

`restrict`は延長の随伴です。したがって、

```julia
julia> restrict(a_fine)
3-element Array{Float64,1}:
 0.125
 0.7875
 0.3125

julia> (P'*a_fine)/2
3-element Array{Float64,1}:
 0.125
 0.7875
 0.3125
```

ここで、2で割ることは入力の平均強度をおおよそ保持します。

ここで見られるように、奇数長の`a_fine`に対して、制限は半分のグリッドポイントでの補間の随伴です。`length(a_fine)`が偶数の場合、制限は1/4および3/4グリッドポイントでの補間の随伴です。これが`l->l÷2 + 1`の動作の起源となります。

この定義の一つの結果は、エッジがゼロに向かって移動することです：

```julia
julia> restrict(ones(11))
6-element Array{Float64,1}:
 0.75
 1.0
 1.0
 1.0
 1.0
 0.75
```

いくつかのアプリケーション（例：画像登録）では、エッジをトリミングすることが有用である場合があります。
