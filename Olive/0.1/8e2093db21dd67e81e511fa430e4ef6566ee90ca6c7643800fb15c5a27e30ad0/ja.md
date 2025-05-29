```julia
build(c::AbstractConnection, ...) -> ::AbstractComponent
```

`build` 関数は、`Olive` バックエンドとフロントエンドの間の翻訳レイヤーとして使用されます。クライアントは HTML であり、これらの関数は与えられたパラメトリック型の HTML 表現を構築します。この関数を新しいメソッドで拡張することで、新しいセル、ディレクトリ、およびプロジェクトを簡単に作成できます。

```julia
# build のための拡張可能なメソッド:

build(c::Connection, om::OliveModifier, oe::OliveExtension{<:Any}) # 拡張をロード

build(c::Connection, env::Environment{<:Any}) # 環境拡張

build(c::Connection, dir::Directory{<:Any}) # ディレクトリ拡張

build(c::AbstractConnection, cm::ComponentModifier, p::Project{<:Any}) # プロジェクト拡張

build(c::Connection, cell::Cell{:dir}, d::Directory{<:Any}; bind::Bool = true) # ファイルセル

build(c::Connection, cm::ComponentModifier, cell::Cell{<:Any}, proj::Project{<:Any}) # コードセル
```

例えば、`:code` セルは `Method` `build(::Connection, ::ComponentModifier, ::Cell{:code}, ::Project{<:Any})` を使用して `Olive` に追加されます。

  * 参照: `start`, `on_code_build`, `cell_highlight!`, `cell_bind!`, `evaluate`, `Cell`, `Project`
