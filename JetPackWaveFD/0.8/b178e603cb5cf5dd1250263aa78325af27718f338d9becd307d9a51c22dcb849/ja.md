```
g = Ginsu(r0, dr, nr, sour, recr, padr, ndamp; dims=(:z,:y,:x), stencilhalfwidth=2, vector_width=8)
```

与えられたショットのモデルアパーチャを定義するGinsuオブジェクトを作成します。 `g`は、`sub`および`sub!`メソッドを使用して地球モデルをサブセット化するために使用され、`super`、`super!`および`super_accumulate!`メソッドを使用して逆操作を提供します。地球モデルサブセットのパディングは、ソースおよびレシーバーの位置、パディング`padr`およびダンピング領域`ndamp`パラメータから決定されます。

# 必須パラメータ[1,2]

  * `r0::NTuple{N,Real}` 各モデル次元におけるモデルの原点
  * `dr::NTuple{N,Real}` 各モデル次元におけるモデルセルの幅
  * `nr::NTuple{N,Int}` 各モデル次元におけるモデルセルのカウント
  * `sour::NTuple{N,Vector{Float}}` 各モデル次元におけるソースの位置
  * `recr::NTuple{N,Vector{Float}}` 各モデル次元におけるレシーバーの位置
  * `padr::NTuple{N,NTuple{Real,Real}}` 各モデル次元における調査アパーチャを超えたパディング[3,4]
  * `ndamp::NTuple{N,NTuple{Int,Int}}` 各モデル次元における吸収境界のダンピング領域[3,4]

# 名前付きオプションパラメータ

  * `dim=(:z,:y,:x)` 軸の順序、デフォルトは`z`が速く、`x`が遅い
  * `stencilhalfwidth=0` 自由表面がある場合、`stencilhalfwidth`、`padr`、および`ndamp`を適切に設定します。これにより、自由表面の上に`stencilhalfwidth`セルが追加され、ミラーリングされたモデルをコピーして自由表面境界条件を実装できるようになります。
  * `vector_width=8` コードのベクトル化に必要な幅を設定し、各次元に対して`size(ginsu)`を`vector_width`で割った余りがゼロになることを保証します。

# 型指定

  * `g.lextrng` はGinsuモデルサブセットの論理（1ベース）インデックスです
  * `g.lintrng` はGinsuモデルサブセット内部の論理（1ベース）インデックスです
  * `rₒ` はGinsuモデルサブセットの物理的原点です
  * `δr` はグリッドセルのサイズです

# 注意事項

1. `N` はモデル次元の数です
2. `rₒ[i]` はi番目のモデル次元に沿ったモデルの原点です
3. モデルのパディングは`padr`と`ndamp`の組み合わせです
4. `padr[i][1]` は次元の開始のパディングであり、`padr[i][2]` は終了のパディングです。同様のことが`ndamp`にも当てはまります。

## 例（自由表面）

```
o---------------c---x--------------x---c-------o
|               |   |              |   |       |
|               |   |              |   |       |
|               |   |              |   |       |
|               |   |              |   |       |
|               |   x--------------x   |       |
|               |                      |       |
o---------------c----------------------c-------o
```

  * `o` は元のモデルを示します
  * `c` はGinsuモジュールサブセットを示します
  * `x` はGinsuモデルサブセット内部を示します
  * GinsuモデルサブセットとGinsuモデルサブセット内部の間にある領域は、吸収境界領域です。
