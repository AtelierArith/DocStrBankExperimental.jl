```
deploy(
    source, [dir="."], [targets...=html];
    versioned=true,
    named=false,
    force=false,
    label=nothing,
)
```

指定された `targets` リストを使用して `dir` ディレクトリ内に `source` をビルドします。`source` は `Module` または `Project.toml` パスを表す `String` のいずれかです。

キーワード引数を使用して、結果のディレクトリ構造を制御できます。

{#keywords}

  * `versioned` と `named`。

    これらのキーワードは、ビルドされたファイルを `dir` のバージョン付きサブディレクトリまたは名前付きサブディレクトリに配置します。両方を指定することも可能ですが、その場合は名前がバージョンを上書きします。

    `name` と `version` の値は、プロジェクトの `Project.toml` ファイルに提供されたものから取得されます。これらの値が指定されていない場合、「デプロイメント」は失敗します。
  * `force` は、ビルド前に計算されたビルドパスを削除します。すでに存在する場合に限ります。
  * `label` は、完成したビルドをコピーするための一時的なフォルダ名を指定します。これは、時間の経過とともに変化する「dev」や「stable」などのドキュメントの「トラッキング」バージョンをビルドするために使用できますが、正確なバージョン付きビルドを保持します。

## 例

以下の例では、私たちのプロジェクトは `Publish` パッケージになります。これは、他のプロジェクトソース（Juliaパッケージや単純な `Project.toml` ファイルなど）に置き換えることができます。

```julia
deploy(Publish, "build")
```

現在のディレクトリの `"build"` サブディレクトリに出力を書き込みます。HTMLコンテンツを含む `build/<version>` フォルダが作成されます。

```julia
deploy(Publish, "build", pdf)
```

上記と同じことを行いますが、[`pdf`](#) 出力をビルドします。

```julia
deploy(Publish, "all-docs", pdf, html)
```

または、すべてを一度にビルドします。

キーワード引数は、ビルドの他の側面を制御します。[上記](#keywords)のように。例えば、

```julia
deploy(Publish, "ecosystem"; named=true)
```

は `Publish` ドキュメントを `ecosystem/Publish/<version>` サブディレクトリにビルドします。
