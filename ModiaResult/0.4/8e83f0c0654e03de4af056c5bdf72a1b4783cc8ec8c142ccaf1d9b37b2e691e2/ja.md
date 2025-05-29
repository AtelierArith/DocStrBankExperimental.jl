```
(resultデータ構造`result`と、配列範囲インデックスの有無にかかわらず変数`ysigName::AbstractString`（例えば`ysigName = "a.b.c[2,3:5]"`）およびオプションの変数名`xsigName::AbstractString`をx軸に指定して、次のものを返します。

  * `xsig::Vector{T1<:Real}`: 単位のないx軸信号のベクトル。セグメントは連結され、NaNで区切られます。
  * `xsigLegend::AbstractString`: 利用可能な場合は単位を含むx軸名からなるx軸の凡例。
  * `ysig::Vector{T2}`または`::Matrix{T2}`: 単位のない値のベクトルまたは行列としてのy軸信号。例えば、`ysigName = "a.b.c[2,3:5]"`の場合、`ysig`は`"a.b.c[2,3]", "a.b.c[2,4]", "a.b.c[2,5]"`の変数値に対応する3列の行列で構成され、（潜在的な）単位は取り除かれます。セグメントは連結され、NaNで区切られます。
  * `ysigLegend::Vector{AbstractString}`: `ysig`がベクトルの場合は`ysigLegend[1]`が`ysig`の凡例であり、`ysig`が行列の場合は`ysigLegend[i]`が`ysig`のi番目の列の凡例です。例えば、変数`"a.b.c"`が単位`m/s`を持つ場合、`ysigName = "a.b.c[2,3:5]"`は`ysigLegend = ["a.b.c[2,3] [m/s]", "a.b.c[2,4] [m/s]", "a.b.c[2,5] [m/s]"]`を生成します。
  * `ysigType::`[`SignalType`](@ref): `ysig`の信号タイプ（`ModiaResult.Continuous`または`ModiaResult.Clocked`のいずれか）。

`ysigName`が無効であるか、信号値が利用できない場合、関数は`(nothing, nothing, nothing, nothing, nothing)`を返し、警告メッセージを表示します。
```
