```
struct Parameters <: AbstractDict{Symbol, Any} ⋯ end
```

モデルパラメータのコンテナです。これは、キーがパラメータ名である `Dict` として機能します。単純なパラメータ値は直接保存されます。特別なパラメータは他のパラメータに依存しており、その依存関係を追跡するために適切なデータ構造にラップされています。特別なパラメータには、エイリアスとリンクの2種類があります。

個々のパラメータには、ドット表記とブラケット表記の2つの異なる方法でアクセスできます。

ドット表記による読み取りアクセスは [`peval`](@ref) を呼び出しますが、ブラケット表記は呼び出しません。これは単純なパラメータには違いはありません。特別なパラメータの場合、ブラケット表記によるアクセスはその内部構造を返しますが、ドット表記によるアクセスは他のパラメータに依存した現在の値を返します。

書き込みアクセスは、ドット表記とブラケット表記の両方で同じです。新しいパラメータ値は、単純なパラメータの場合に直接割り当てられます。エイリアスパラメータを作成するには、[`@alias`](@ref) マクロを使用します。リンクパラメータを作成するには、[`@link`](@ref) マクロを使用します。

関連情報: [`ModelParam`](@ref), [`peval`](@ref), [`@alias`](@ref), [`@link`](@ref), [`update_links!`](@ref).
