## 配列

配列は信号として扱うことができます。最初の次元は時間で、2番目はチャネルです。

[`AxisArrays`](https://github.com/JuliaArrays/AxisArrays.jl)は、`time`というラベルの付いた軸と1つまたは0の追加の軸を持っている場合、信号として扱うことができます。時間次元は、`step`関数が定義されたオブジェクト（例えば、任意の`AbstractRange`）を使用して表現する必要があります。
