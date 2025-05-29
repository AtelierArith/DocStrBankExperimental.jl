```
generateSPDX(docData::spdxCreationData= spdxCreationData(), sbomRegistries::Vector{<:AbstractString}= ["General"])
```

SPDX形式でソフトウェアBOMを生成します。デフォルトでは、SBOMはアクティブな環境内のすべてのパッケージとアーティファクトを説明し、ダウンロード情報を取得するためにGeneralレジストリを使用します。

別のレジストリを使用したり、複数のレジストリを検索したい場合は、2つの引数を指定して`generateSPDX`を呼び出すだけです。

たとえば、Generalレジストリと「PrivateRegistry」という別のレジストリを使用してユーザー環境SBOMを作成するには、次のように入力します。

```julia-repl
sbom= generateSPDX(spdxCreationData(), ["PrivateRegistry", "General"]);
```
