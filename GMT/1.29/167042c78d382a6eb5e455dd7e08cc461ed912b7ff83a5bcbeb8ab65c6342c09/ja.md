```
J = bwskell(I::Union{GMTimage{<:UInt8, 2}, GMTimage{<:Bool, 2}}; type::Int=1, maxiters::Int=0, conn::Int=4)::GMTimage
```

2次元のバイナリ画像内のすべてのオブジェクトを線に縮小します。

2次元のバイナリ画像 `I` 内のすべてのオブジェクトを1ピクセル幅の曲線に縮小し、画像の本質的な構造を変更することなく行います。このプロセスはスケルトン化と呼ばれ、トポロジーを保持しながら中心線を抽出します。

### 引数

  * `I::Union{GMTimage{<:UInt8, 2}, GMTimage{<:Bool, 2}}`: 入力画像。

### キーワード引数

  * `type::Int=1`: 前景を細くするための1（通常の状況）、または背景を細くするための2。
  * `maxiters::Int=0`: 許可される最大反復回数。0を使用すると完了するまで反復します。
  * `conn::Int=4`: 4接続のための4、8接続のための8。

### 戻り値

スケルトンを持つ、`I` と同じタイプの新しい `GMTimage`。

### 例

```julia
I = gmtread(TESTSDIR * "assets/bone.png");
J = bwskell(I);
grdimage(I, figsize=6)
grdimage!(J, figsize=6, xshift=6, show=true)
```
