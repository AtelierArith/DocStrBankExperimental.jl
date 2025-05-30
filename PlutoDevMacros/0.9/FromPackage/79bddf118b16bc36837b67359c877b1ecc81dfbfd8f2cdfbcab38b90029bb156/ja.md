```
@frompackage target import_block
```

このマクロは、ローカルパッケージ（`target`パスから派生したもので、`AbstractString`または`@raw_str`である可能性があります）を取り込み、現在のPlutoワークスペースのサブモジュールとしてロードし、`import_block`内のさまざまなimport/using文を処理して、ローカルパッケージからノートブックワークスペースに変数/関数を抽出します。

主な用途は、実行中のPlutoノートブック内で開発中のローカルパッケージをロードし、プロトタイピングとテストを容易にすることです。

Plutoノートブックセル内の次のjuliaコード：

```julia
@frompackage local_package_path begin
	import ^: *
	using >.LocalDependency
end
```

は、`local_package_path`にあるパッケージのメインモジュール定義コードを取り込み、ノートブックワークスペースに対応するモジュールを作成し、その中で定義されたすべての名前をインポートします（これは`import ^:*`文の役割です）。

さらに、`LocalDependency`というパッケージをロードします（これはローカルパッケージの依存関係である必要があります）。これは、ノートブック内で`using LocalDependency`コードが使用されたかのように動作しますが、ノートブック環境に`LocalDependency`を追加することはありません。

詳細については、パッケージの[ドキュメント](https://disberd.github.io/PlutoDevMacros.jl/dev/frompackage/introduction/#Introduction)を参照してください。

また、[`@fromparent`](@ref)も参照してください。
