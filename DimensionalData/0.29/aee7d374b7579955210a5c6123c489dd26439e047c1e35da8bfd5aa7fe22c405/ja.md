```
AbstractDimStack
```

次元スタックの抽象スーパタイプです。

これらは複数のデータ層を持ちますが、次元を共有します。

特に、その動作は `DimArray` と `NamedTuple` の間に位置します：

  * `dimstack[:symbol]` のように `Symbol` でインデックスを指定すると、`DimArray` 層が返されます。
  * 繰り返し処理と `map` は、`Symbol` でインデックス指定された配列層に適用されます。
  * `getindex` と多くの基本メソッドは、`DimArray` のように適用されます - 常に `map` を使用する必要がないようにするためです。

この設計は、多層で混合次元のオブジェクトを扱う際に非常に簡潔なコードを提供します。しかし、最初は驚くかもしれません - 最も驚くべき結果は、`dimstack[1]` がすべての層の最初のインデックスの値の `NamedTuple` を返すのに対し、`first(dimstack)` はイテレータの最初の値 - 最初の層の `DimArray` を返すことです。

具体的な実装については [`DimStack`](@ref) を参照してください。ほとんどのメソッドは抽象タイプに定義されています。

`AbstractDimStack` を拡張するには、[`rebuild`](@ref) の引数およびキーワードバージョンと、[`rebuild_from_arrays`](@ref) を実装してください。

`AbstractDimStack` のコンストラクタは `NamedTuple` を受け入れなければなりません。
