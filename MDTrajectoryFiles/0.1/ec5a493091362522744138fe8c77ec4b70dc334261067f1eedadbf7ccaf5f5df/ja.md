```
XtcFile
```

xtcファイルへのハンドル。読み取りモードで開くと、ファイルをスキャンし、フレームへのオフセットを保存して高速なランダムアクセスを可能にします。     

# 有用なフィールド（すべて読み取りモードで開くと初期化されます）

  * natoms::Int
  * nframes::Int
  * time::Vector{Float32}(nframes)

# コンストラクタ

```
XtcFile(name::AbstractString, mode::AbstractString)
```

modeは通常の文字列r,w,aです。

# 単位

  * 時間: ps
  * 距離: Å
