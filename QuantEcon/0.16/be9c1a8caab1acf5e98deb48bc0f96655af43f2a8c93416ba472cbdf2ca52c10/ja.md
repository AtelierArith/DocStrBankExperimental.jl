d次元関数 `f` を、次元 i に対して `a[i]` と `b[i]` で定義された矩形の下限と上限で積分します。使用する点の数は `n[i]` です。

##### 引数

  * `f::Function` 積分する関数。この関数は、最初の引数として各次元に沿った点を表す行列（各次元が列）を受け取る必要があります。関数に渡す必要がある他の引数は `args...` と `kwargs...` でキャッチされます。
  * `n::Union{Int, Vector{Int}}` : 各次元に沿った望ましいノードの数
  * `a::Union{Real, Vector{Real}}` : 各次元に沿った下端点
  * `b::Union{Real, Vector{Real}}` : 各次元に沿った上端点
  * `kind::AbstractString("lege")` 積分の種類を指定します。有効な値は次のとおりです：

      * `"lege"` : ガウス・レジェンドル
      * `"cheb"` : ガウス・チェビシェフ
      * `"trap"` : 台形法
      * `"simp"` : シンプソン法
      * `"N"` : ニーダーライター等分配列
      * `"W"` : ワイル等分配列
      * `"H"` : ハーバー等分配列
      * `"R"` : モンテカルロ
      * `args...(Void)`: `f` に渡す追加の位置引数
      * `;kwargs...(Void)`: `f` に渡す追加のキーワード引数

##### 戻り値

  * `out::Float64` : `[a, b]` によって形成されるハイパーキューブ上の `f` の積分を近似するスカラー

##### 参考文献

Miranda, Mario J, and Paul L Fackler. Applied Computational Economics and Finance, MIT Press, 2002.
