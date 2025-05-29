```
CyclicArray
```

CyclicArrayデータ構造。利用可能なコンストラクタ：

```
CyclicArray(data::AbstractArray{T,N}, connections::AbstractArray)
```

xの接続を持つ新しいCyclicArrayを生成するには：

```
CyclicArray(x::CyclicArray)
```

接続を持つ新しいCyclicArrayを生成するには：

```
CyclicArray(connections)
```

yの接続とxからのデータを持つ新しいCyclicArrayを生成するには：

```
CyclicArray(x::AbstractArray,y::CyclicArray)
```

事前定義された接続を持つ新しいCyclicArrayを生成するには：

```
CyclicArray(x::AbstractArray,str::String)
```

利用可能なオプション：

"1D" - 一次元配列、1つの面

"1D2F" - 一次元配列、2つの面

"2D" - 二次元配列、1つの面

"2DXY" - 二次元配列、1つの面、x-y方向を切り替え

"2DFL" - 二次元配列、1つの面、側面を反転

"3D" - 三次元配列、1つの面

"3DXY" - 三次元配列、1つの面、x-y方向を切り替え

"cubed" - 立方体の球、三次元配列、6つの面

"cubed2D" - 立方体の球、二次元配列、6つの面
