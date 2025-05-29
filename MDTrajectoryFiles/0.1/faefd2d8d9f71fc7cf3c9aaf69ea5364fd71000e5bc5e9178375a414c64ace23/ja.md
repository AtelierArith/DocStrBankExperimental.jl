```
DcdFile
```

Dcdファイルへのハンドル。読み取りモードで開くと、ヘッダーを読み込み、フレームへのオフセットを保存して高速なランダムアクセスを可能にします。     

# 有用なフィールド、すべて読み取りモードで開くと初期化されます。

  * natoms::Int
  * nframes::Int
  * time::Vector{Float32}(nframes)

# コンストラクタ

```
DcdFile(name::AbstractString, mode::AbstractString)
```

modeは通常の文字列 r,w,a です。
