# SwapStreams.jl

[![Build Status](https://travis-ci.com/Tokazama/SwapStreams.jl.svg?branch=master)](https://travis-ci.com/Tokazama/SwapStreams.jl) [![stable-docs](https://img.shields.io/badge/docs-stable-blue.svg)](https://Tokazama.github.io/SwapStreams.jl/stable) [![dev-docs](https://img.shields.io/badge/docs-dev-blue.svg)](https://Tokazama.github.io/SwapStreams.jl/dev) [![codecov](https://codecov.io/gh/Tokazama/SwapStreams.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/Tokazama/SwapStreams.jl)

Base Juliaライブラリの`read(io::IO, T)`のドキュメントから...

> Juliaはエンディアンを自動的に変換しません。この目的のために`ntoh`または`ltoh`を使用してください。


...しかし、`SwapStreams`はそうします！

`SwapStreams`は、任意のI/Oストリームをラップするシンプルな型（`SwapStream`）をエクスポートします。一度構築されると、`SwapStream`は適切な場合にすべての読み書き操作でバイトスワップを行います。

```jldoctest README
julia> using SwapStreams

julia> s = SwapStream(IOBuffer());  # バイトスワッピングが必要だと仮定

julia> write(s, [1:10...]);         # バッファに書き込む前に各要素をバイトスワップ

julia> seek(s, 0);

julia> read!(s.io, Vector{Int}(undef, 10))  # バッファからの生データ
10-element Vector{Int64}:
  72057594037927936
 144115188075855872
 216172782113783808
 288230376151711744
 360287970189639680
 432345564227567616
 504403158265495552
 576460752303423488
 648518346341351424
 720575940379279360


julia> seek(s, 0);

julia> read!(s, Vector{Int}(undef, 10))  # バッファからのバイトスワップされたデータ
10-element Vector{Int64}:
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10

```

`SwapStream`にバイトスワップを行うかどうかを、構築時に`true`または`false`を指定することで直接指示できます。あるいは、エクスポートされた定数`BigEndian`と`LittleEndian`を使用して、ストリームがビッグエンディアンかリトルエンディアンかを指定することもできます。

```jldoctest README
julia> using SwapStreams

julia> io = IOBuffer();

julia> SwapStream(true, io) == SwapStream(io)  # バイトスワップを行う
true

julia> SwapStream(false, io) ==    # 明示的にバイトスワップを行わない
       SwapStream(ifelse(ENDIAN_BOM == BigEndian, BigEndian, LittleEndian), io)  # ストリームがシステムと同じエンディアンタイプなのでスワップしない
true
```

ストリームのエンディアンをシステムと同じに設定しているため、バイトスワッピングは行われません。
