```
Ik = kmeans(I::GMTimage, k=5; seeds=nothing, maxiter=100, tol=1e-7, V=false) -> GMTimage
```

RGB画像`I`に対してk-meansクラスタリングを計算します。固定数のクラスタを生成し、それぞれのクラスタには中心が関連付けられ、各RGB色は最も近い中心に割り当てられます。

  * `I`: 入力$GMTimage$オブジェクト。
  * `k`: 教師なし分類を使用する際のクラスタの数。
  * `seeds`: 教師あり分類の場合、これはクラスタ中心の色を持つMx3 UInt8行列です。アルゴリズムはこれらのMシード色の周りに画像内のすべての色を集約します。注意：提供された場合、このオプションは`k`をリセットします。
  * `maxiter`: アルゴリズムが解に達するまでに実行できる最大反復回数。
  * `tol`: 収束中の目的関数の最小許容変化を設定します。2つの条件のいずれかが最初に満たされると、反復プロセスは停止します。
  * `V`: 反復ループの最後にいくつかの情報を印刷します（反復回数、費やした時間）。

```
kmeans(X::Union{GMTdataset, Matrix{<:Real}}, k=3; seeds=nothing, maxiter=100, tol=1e-7,
       raw::Bool=false, V=false) -> Vector{GMTdataset} | idx, centers, counts
```

このメソッドは、M-by-d行列または$GMTdataset$を受け入れ、列はデータポイントを、行は`d`次元のデータポイントを表します。

  * `raw`: `false`の場合、戻り値のデータは入力データで見つかった各クラスタの$GMTdataset$のベクトルになります。`raw=true`の場合、次のように返します：`idx, centers, counts`、ここで

      * `idx`: 各データポイントのクラスタへの割り当てを示す整数のベクトル（`idx`ベクトル内の位置による）。
      * `centers`: 各クラスタの中心を持つk-by-d行列。
      * `counts`: 最初の列にクラスタ番号、2番目の列にそのクラスタ内の要素数を持つ整数の行列。

### 例

```jldoctest
    D = gmtread(GMT.TESTSDIR * "iris.dat");
	Dk = kmeans(D, k=3)		# 教師なしでデータを3つのクラスタに分割します。
```
