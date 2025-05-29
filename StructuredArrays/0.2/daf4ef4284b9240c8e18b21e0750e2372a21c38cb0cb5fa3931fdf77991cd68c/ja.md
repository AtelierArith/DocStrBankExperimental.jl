```
mesh = CartesianMesh{N}(step, origin = nothing)
```

は、与えられた `step`（連続するノード間の距離）と `origin`（座標の原点）を持つ `N` 次元の直交メッシュのノードの座標を生成する呼び出し可能なオブジェクトを生成します。`step` または `origin` のいずれかが `N` タプルである場合、パラメータ `N` は省略可能です。メッシュオブジェクトを `i = (i1,i2,...)` で呼び出すと、ノードの `N` インデックスが得られます：

```
mesh(i) = step .* i             # `origin` が `nothing` の場合
mesh(i) = step .* (i .- origin) # それ以外の場合
```

ブロードキャスティングルールのおかげで、`step` と `origin` のそれぞれはスカラーとして指定でき、すべての次元に対して同じパラメータであると仮定できます。それ以外の場合は `N` タプルとして指定します。`origin` は `nothing`（デフォルト）にすることもでき、メッシュの原点がインデックス `(0,0,...)` にあると仮定します。実装では、ノードの座標を計算するために使用される正確な式は、さまざまな可能なケースに最適化されています。その結果、`origin` を `0` または `0` の `N` タプルとして指定すると、同じ座標を持つメッシュが得られますが、`origin = nothing` の場合よりもオーバーヘッドが大きくなります。

`step` は単位を持つことができます（次元ごとに異なる可能性があります）が、`origin` は単位なし（整数または実数）でなければなりません。メッシュパラメータの値は、`step(mesh)` または [`origin(mesh)`](@ref StructuredArrays.Meshes.origin) を呼び出すことで取得できます。すべてのケースで `N` 次元の *step* と *origin* を取得するには、`step(Tuple,mesh)` または `origin(Tuple,mesh)` を呼び出します。メッシュによって保存される `step` と `origin` の値は、座標を計算する際の操作数を減らすために、構築時に変換される場合があります。この最適化は、すべてのインデックスが `Int` として指定されることを前提としていますが、分数インデックス（すなわち実数）も受け入れられます。

典型的な使用法は、直交メッシュを `StructuredArray` でラップして、有限サイズの直交メッシュのノードの座標を値とする抽象配列を構築することです。例えば：

```
grid = StructuredArray(CartesianMesh{N}(step, origin), inds...)
```

ここで `inds...` はメッシュの *shape*（インデックスおよび/または次元）です。これは、[`CartesianMeshArray`](@ref StructuredArrays.Meshes.CartesianMeshArray) を呼び出すことでも行えます：

```
grid = CartesianMeshArray(inds...; step, origin=nothing)
```
