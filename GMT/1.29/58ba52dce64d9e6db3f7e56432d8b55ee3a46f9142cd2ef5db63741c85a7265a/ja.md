```
Ibw = binarize(I::GMTimage, threshold::Int=0; band::Int=1, threshold::Int=0, revert::Bool=false, bool::Bool=false) -> GMTimage
```

または

```
Ibw = binarize(I::GMTimage, threshold::Vector{Int}; band::Int=1, revert::Bool=false, bool::Bool=false) -> GMTimage
```

画像をしきい値を使用してバイナリ画像（白黒）に変換します。

### 引数

  * `I::GMTimage`: UInt8型の入力画像。
  * `threshold::Int`: 範囲[0 255]の数値。デフォルト（0）が保持され、キーワード`threshold`が使用されない場合、しきい値は$isodata$メソッドを使用して計算されます。 あるいは、範囲[0 255]の2つの数値のベクトルを使用することもできます。この場合、しきい値は最初の値に設定され、2番目の値はしきい値範囲の上限を設定するために使用されます。つまり、2つの値の間の値は255に設定され、残りは0に設定されます（または`bool`キーワードが`true`に設定されている場合はそれぞれ`true`とfalseになります）。この2番目の形式では、`threshold`キーワードは存在しないことに注意してください。

### キーワード引数

  * `band`: `I`画像に複数のバンドがある場合、`band`を使用してどのバンドをバイナライズするかを指定します。デフォルトでは最初のバンドが使用されます。
  * `bool`: `true`の場合、出力画像はBool型になります。それ以外の場合はUInt8型になります。
  * `threshold`: 位置引数`threshold`の代替キーワード引数。つまり、`binarize(I, =??)`または`binarize(I, threshold=??)`のいずれかを使用できます。
  * `revert`: `true`の場合、しきい値未満の値は255に設定され、しきい値以上の値は0に設定されます。

### 戻り値

新しい$GMTimage$。

### 例

```jldoctest
I = gmtread(GMT.TESTSDIR * "assets/coins.jpg");
Ibw = binarize(I, band=1)
# 2つを並べて表示
grdimage(I, figsize=6)
grdimage!(Ibw, figsize=6, xshift=6.1, show=true)
```
