```
CuDim3(x)

CuDim3((x,))
CuDim3((x, y))
CuDim3((x, y, x))
```

3つの整数から構成される次元を指定するために使用される型で、それぞれ `x`、`y`、`z` 次元を表します。指定されていない次元はデフォルトで `1` になります。

しばしば `CuDim` 型エイリアスを通じて引数として受け入れられます。例えば、[`cudacall`](@ref) や [`CUDA.launch`](@ref) の場合、明示的な `CuDim3` オブジェクトを構築することなく、次元を単純な整数またはタプルとして渡すことができます。
