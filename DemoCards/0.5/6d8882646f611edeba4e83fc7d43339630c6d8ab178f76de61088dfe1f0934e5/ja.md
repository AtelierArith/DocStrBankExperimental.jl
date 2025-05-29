```
makedemos(source::String;
          root = "<current-directory>",
          src = "src",
          build = "build",
          branch = "gh-pages",
          edit_branch = "master",
          credit = true,
          throw_error = false) -> page_path, postprocess_cb
```

`source`のデモページを作成し、生成されたインデックスファイルへのパスを返します。

処理パイプライン：

1. フォルダ構造`source`を分析し、すべての利用可能な設定を読み込みます。
2. アセットをコピーします。
3. デモファイルを前処理し、保存します。
4. カバー画像を保存/コピーします。
5. URLリダイレクションを含む後処理コールバック関数を生成します。

!!! warning
    デフォルトでは、`makedemos`はすべての必要なファイルを`docs/src/`に生成します。これは、`makedemos`に渡すデータを`docs/src/`に配置しないことを意味します。推奨されるのは、`docs/`内にフォルダを置くことです。例えば、`docs/quickstart`は良い選択です。


# 入力

  * `source`: デモのルートページへのディレクトリパス; `docs`に対して相対的です。

# 出力

  * `page_path`: デモページのインデックスへのパス。これを直接`makedocs`に渡すことができます。
  * `postprocess_cb`: 後処理のためのコールバック関数。`makedocs`の*後*に`postprocess_cb()`を呼び出すことができます。
  * `theme_assets`: `Documenter.HTML`に渡す必要があるスタイルシートアセット。デモページにテーマがない場合、`nothing`を返します。

# キーワード

  * `root::String`: `Documenter`の設定と等しくする必要があります。通常、これは`docs/make.jl`ファイル内でこの関数が呼ばれる場合、`"docs"`です。
  * `src::String`: `Documenter`の設定と等しくする必要があります。デフォルトでは`"src"`です。
  * `build::String`: `Documenter`の設定と等しくする必要があります。デフォルトでは`"build"`です。
  * `edit_branch::String`: `Documenter`の設定と等しくする必要があります。デフォルトでは`"master"`です。
  * `branch::String`: `Documenter`の設定と等しくする必要があります。デフォルトでは`"gh-pages"`です。
  * `credit::Bool`: `"このページは...によって生成されました"`の情報を表示するには`true`にします。デフォルトでは`true`です。
  * `throw_error::Bool`: juliaデモビルドが失敗した場合にエラーをスローするには`true`にします。そうでない場合は、警告とともにビルドを続行します。
  * `filter_function::Function`: 各潜在的な`DemoCard`に渡される関数で、関数がfalseを返すとカードは除外されます。デフォルトでは、すべての潜在的なカードが含まれます。

# 例

以下は、あなたが始めるための最も簡単な例です：

```julia
# 1. docs/srcにデモファイルを前処理して生成
examples, postprocess_cb, demo_assets = makedemos("examples")

assets = []
isnothing(demo_assets) || (push!(assets, demo_assets))

# 2. 標準のDocumenterパイプラインを実行
makedocs(format = Documenter.HTML(assets = assets),
         pages = [
             "Home" => "index.md",
             examples
         ])

# 3. makedocsの後に後処理を行う
postprocess_cb()
```

デフォルトでは、デモのインデックスページは生成されません。これを有効にし、インデックスページがどのように生成されるかを構成するには、"examples/config.json"を作成する必要があります。その内容は以下のようになります：

```json
{
    "theme": "grid",
    "order": [
        "basic",
        "advanced"
    ]
}
```

`config.json`の設定方法の詳細については、[`DemoCards.DemoPage`](@ref)を確認してください。
