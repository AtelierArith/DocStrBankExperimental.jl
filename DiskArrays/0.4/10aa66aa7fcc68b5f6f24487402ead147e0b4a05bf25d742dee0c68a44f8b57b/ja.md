# DiskArrays.jl

![ライフサイクル](https://img.shields.io/badge/lifecycle-maturing-blue.svg) [![安定版ドキュメント](https://img.shields.io/badge/docs-stable-blue.svg)](https://juliaio.github.io/DiskArrays.jl/stable) [![開発版ドキュメント](https://img.shields.io/badge/docs-dev-blue.svg)](https://juliaio.github.io/DiskArrays.jl/dev) [![CI](https://github.com/JuliaIO/DiskArrays.jl/actions/workflows/ci.yml/badge.svg)](https://github.com/JuliaIO/DiskArrays.jl/actions/workflows/ci.yml) [![Codecov](https://codecov.io/gh/JuliaIO/DiskArrays.jl/branch/main/graph/badge.svg)](https://codecov.io/gh/JuliaIO/DiskArrays.jl/tree/main)

このパッケージは、単一の読み取り操作に対してかなりのオーバーヘッドを持つn次元配列のようなデータ構造を扱うためのユーティリティのコレクションを提供します。最も重要な例は、Cライブラリを介してアクセスされるハードディスク上のデータを表す配列や、チャンクで圧縮された配列です。これらの配列を`AbstractArray`の直接のサブタイプにすることは推奨されません。なぜなら、AbstractArraysを扱う多くの関数は、単一の値への高速なランダムアクセスを前提としているからです（`getindex`、`show`、`reduce`などの基本的な操作を含む）。

現在サポートされている機能は以下の通りです：

  * 基本と同じルールでの`getindex`/`setindex`（末尾または単一の次元など）
  * `DiskArrays`へのビュー
  * `getindex`を繰り返し呼び出さないフォールバック`Base.show`メソッド
  * 基本データセットのチャンク化を尊重する`mapreduce`および`mapreducedim`の実装。これにより、`sum(a,dims=d)`のような高レベルの集約のパフォーマンスが大幅に向上します。
  * データのチャンクをキャッシュし、その中の値を返すDiskArrayの値に対するイテレータ。これにより、例えば`using DataStructures; counter(a)`の効率的な使用が可能になります。
  * LHSに`DiskArray`がある場合の`broadcast`のカスタマイズ。これにより、少なくとも`a.=5`のような操作が可能で比較的高速になります。

## AbstractDiskArray インターフェース定義

このライブラリを使用してディスクベースの配列を`AbstractDiskArray`にしたいパッケージの著者は、少なくとも以下の関数のメソッドを実装する必要があります：

```julia
Base.size(A::CustomDiskArray)
readblock!(A::CustomDiskArray{T,N},aout,r::Vararg{AbstractUnitRange,N})
writeblock!(A::CustomDiskArray{T,N},ain,r::Vararg{AbstractUnitRange,N})
```

ここで`readblock!`は、単位範囲`r`で定義されたハイパー長方形内の配列`A`のサブセットを読み取ります。結果は`aout`に書き込まれます。`writeblock!`は、`ain`によって与えられたデータを`r`で定義されたAの（ハイパー）長方形に書き込む必要があります。関数を定義する際には、`length(r) == ndims(A)`および`size(ain) == length.(r)`が安全に仮定できます。ただし、境界チェックはDiskArrayの機構によって行われず、現在は実装によって行う必要があります。

ディスク上のデータが矩形のチャンクを持つ基盤ストレージユニットである場合、ブロードキャスト、集約、スパースインデックスなどのいくつかの操作を最適化するために、以下のメソッドを追加で実装する必要があります：

```julia
DiskArrays.haschunks(A::CustomDiskArray) = DiskArrays.Chunked()
DiskArrays.eachchunk(A::CustomDiskArray) = DiskArrays.GridChunks(A, chunksize)
```

ここで`chunksize`はチャンクの長さの整数タプルです。配列が内部チャンク構造を持たない場合は、次のように定義する必要があります。

```julia
DiskArrays.haschunks(A::CustomDiskArray) = DiskArrays.Unchunked()
```

これらのメソッドのみを実装することで、すべての種類の奇妙なインデックスパターン（コロン、ステップ範囲、整数ベクトル、ブールマスク、CartesianIndices、CartesianIndexの配列、これらのすべての混合）を機能させることができ、必要な配列値の矩形バウンディングボックスを読み取って、結果の値を出力配列に再配置することで、できるだけ少ない`readblock!`または`writeblock!`の呼び出しが行われることを保証します。

さらに、DiskArrays.jlは、`A[:,:,[1,1500]]`のようなインデックスに対して、ディスクから不要なデータを読み取って破棄するのを避けるためのスパースインデックスパターンの最適化をいくつか提供します。

# 例

ここでは、通常のAbstractArrayをラップする新しい配列タイプを定義します。定義する唯一のアクセスメソッドは、インデックスが配列の各次元に沿った単位範囲として厳密に与えられる`readblock!`関数です。これは、HDF5、NetCDF、Zarrなどのライブラリで使用される非常に一般的なAPIです。また、イテレーションと集約の計算方法を制御するチャンク化も定義します。データがどのようにアクセスされるかを正確に理解するために、`readblock!`および`writeblock!`関数に追加の印刷ステートメントを追加しました。

```julia
using DiskArrays

struct PseudoDiskArray{T,N,A<:AbstractArray{T,N}} <: AbstractDiskArray{T,N}
  parent::A
  chunksize::NTuple{N,Int}
end
PseudoDiskArray(a;chunksize=size(a)) = PseudoDiskArray(a,chunksize)
haschunks(a::PseudoDiskArray) = Chunked()
eachchunk(a::PseudoDiskArray) = GridChunks(a,a.chunksize)
Base.size(a::PseudoDiskArray) = size(a.parent)
function DiskArrays.readblock!(a::PseudoDiskArray,aout,i::AbstractUnitRange...)
  ndims(a) == length(i) || error("インデックスの数が正しくありません")
  all(r->isa(r,AbstractUnitRange),i) || error("すべてのインデックスが単位範囲ではありません")
  println("インデックス ", join(string.(i)," "), " で読み込み中")
  aout .= a.parent[i...]
end
function DiskArrays.writeblock!(a::PseudoDiskArray,v,i::AbstractUnitRange...)
  ndims(a) == length(i) || error("インデックスの数が正しくありません")
  all(r->isa(r,AbstractUnitRange),i) || error("すべてのインデックスが単位範囲ではありません")
  println("インデックス ", join(string.(i)," "), " に書き込み中")
  view(a.parent,i...) .= v
end
a = PseudoDiskArray(rand(4,5,1))
```

```
サイズ 10 x 9 x 1 のディスク配列
```

これで、すべてのBaseインデックス動作が私たちの配列で機能し、実行される読み取りの数が最小限に抑えられます：

```julia
a[:,3]
```

```
インデックス Base.OneTo(10) 3:3 1:1 で読み込み中

10要素の配列{Float64,1}:
 0.8821177068878834
 0.6220977650963209
 0.22676949571723437
 0.3177934541451004
 0.08014908894614026
 0.9989838001681182
 0.5865160181790519
 0.27931778627456216
 0.449108677620097  
 0.22886146620923808
```

読み取りメッセージからわかるように、`readblock`への呼び出しは1回だけ行われ、これは基盤のCライブラリへの単一の呼び出しにマッピングされます。

```julia
mask = falses(4,5,1)
mask[3,2:4,1] .= true
a[mask]
```

```
3要素の配列{Int64,1}:
 6
 7
 8
```

同様に、集約がデータ型によって定義されたチャンクを尊重することを確認できます：

```julia
sum(a,dims=(1,3))
```

```
インデックス 1:5 1:3 1:1 で読み込み中
インデックス 6:10 1:3 1:1 で読み込み中
インデックス 1:5 4:6 1:1 で読み込み中
インデックス 6:10 4:6 1:1 で読み込み中
インデックス 1:5 7:9 1:1 で読み込み中
インデックス 6:10 7:9 1:1 で読み込み中

1×9×1 配列{Float64,3}:
[:, :, 1] =
 6.33221  4.91877  3.98709  4.18658  …  6.01844  5.03799  3.91565  6.06882
 ````

DiskArrayがブロードキャスト式のLHSにある場合、結果はチャンクごとに書き込まれます：

```

julia va = view(a,5:10,5:8,1) va .= 2.0 a[:,:,1]

```

```

インデックス 5:5 5:6 1:1 に書き込み中 インデックス 6:10 5:6 1:1 に書き込み中 インデックス 5:5 7:8 1:1 に書き込み中 インデックス 6:10 7:8 1:1 に書き込み中 インデックス Base.OneTo(10) Base.OneTo(9) 1:1 で読み込み中

10×9 配列{Float64,2}:  0.929979   0.664717  0.617594  0.720272   …  0.564644  0.430036  0.791838  0.392748   0.508902  0.941583  0.854843      0.682924  0.323496  0.389914  0.761131   0.937071  0.805167  0.951293      0.630261  0.290144  0.534721  0.332388   0.914568  0.497409  0.471007      0.470808  0.726594  0.97107  0.251657   0.24236   0.866905  0.669599      2.0       2.0       0.427387  0.388476   0.121011  0.738621  0.304039   …  2.0       2.0       0.687802  0.991391   0.621701  0.210167  0.129159      2.0       2.0       0.733581  0.371857   0.549601  0.289447  0.509249      2.0       2.0       0.920333  0.76309    0.648815  0.632453  0.623295      2.0       2.0       0.387723  0.0882056  0.842403  0.147516  0.0562536     2.0       2.0       0.107673 ````

## ストライド配列へのアクセス

特定の軸に沿って毎回別の値を読み取るか、任意のストライドを提供したい場合があります。一部のDiskArrayバックエンドは、これらのストライド配列を読み取るための最適化されたメソッドを提供したいかもしれません。この場合、バックエンドは`readblock!(a,aout,r::OrdinalRange...)`およびそれに対応する`writeblock`メソッドを定義でき、これは全データブロックを読み取り、希望する範囲のみを返すフォールバック動作を上書きします。

## eachchunkを実装しない配列

ディスク上に存在するが矩形のチャンクに分割されていない配列があり、`haschunks`トレイトが`Unchunked()`を返します。これらの配列に対してブロードキャストと集約を有効にするために、チャンクサイズは、特定のメモリ制限を超えないように推定されます。このメモリ制限はデフォルトで100MBであり、`DiskArrays.default_chunk_size[]`を変更することで変更できます。その後、配列の要素サイズに基づいてチャンクサイズが計算されます。ただし、要素型のサイズが未定義である場合（例えば、文字列や可変長ベクトルの場合）もあります。この場合、特定のコンテナ型に対して`DiskArrays.element_size`関数をオーバーロードし、近似要素サイズ（バイト単位）を返すことができます。そうでない場合、要素のサイズは単に`DiskArrays.fallback_element_size`に格納されている値と等しいと仮定され、デフォルトは100バイトです。

[ci-img]: https://github.com/JuliaIO/DiskArrays.jl/workflows/CI/badge.svg [ci-url]: https://github.com/JuliaIO/DiskArrays.jl/actions?query=workflow%3ACI [codecov-img]: http://codecov.io/github/JuliaIO/DiskArrays.jl/coverage.svg?branch=main [codecov-url]: (http://codecov.io/github/JuliaIO/DiskArrays.jl?branch=main)
