```
SwapStream([file_endianness],  io)
```

ファイルエンディアンタイプとIOストリームを指定すると、適切なエンディアンタイプに自動的にバイトスワップするタイプを返します。

## 例

```jldoctest
julia> using SwapStreams

julia> s = SwapStream(IOBuffer());  # バイトスワッピングが必要であると仮定

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
