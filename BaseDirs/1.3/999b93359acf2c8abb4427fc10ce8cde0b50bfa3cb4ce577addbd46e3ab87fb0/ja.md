```
 プロジェクト
```

「プロジェクト」の表現、すなわちプラットフォームに適したプロジェクトパスを生成するために使用される命名情報の基本的なコンポーネント。

```
Project(name::Union{AbstractString, Module};
        org::AbstractString="julia", qualifier::AbstractString="lang")
```

必要な情報と、それを利用するプラットフォームは以下の通りです：

  * `name`、プロジェクトの名前（Linux、MacOS、Windows）
  * `org`（`"julia"`）、プロジェクトが属する組織（MacOS、Windows）
  * `qualifier`（`"org"`）、組織の性質、通常はTLD（MacOS）

結果として得られる「プロジェクトパスコンポーネント」は以下のいずれかの形式を取ります：

| プラットフォーム |                プロジェクトパス形式 |
| --------:| -------------------------:|
|    Linux |            `"$org/$name"` |
|    MacOS | `"$qualifier.$org.$name"` |
|  Windows |            `"$org\$name"` |
