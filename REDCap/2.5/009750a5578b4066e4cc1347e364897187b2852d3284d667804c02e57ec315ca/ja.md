REDCap API メソッドは、名前付きの Julia 関数として定義されています。

REDCap API 呼び出しには、一般的に `content` と `action` パラメータが含まれます。

REDCap.jl では、これらは内部で管理され、引数として渡す必要はありません。関数名は一般的にこれらの組み合わせに対応しています（例：`delete_records()` は `content=record` と `action=delete` を渡します）。

インポートまたはエクスポートの場合、REDCap アクションパラメータは一般的にありません。代わりに、アクションパラメータのない API 呼び出しは、データパラメータがある場合はインポートリクエストとして解釈され、ない場合はエクスポートリクエストとして解釈されます。名前付き関数の期待される動作を保持するために、REDCap.jl のインポート関数は `data` 引数を必要とし、エクスポート関数は受け入れません。

関数のドキュメント文字列は、Julia 関数の使用方法を示しています。対応する REDCap メソッドの詳細な仕様については、公式ドキュメントを参照してください。

## 構文

各 REDCap メソッドは、共通の命名規則に従った複数のパラメータを受け入れます。REDCap.jl は、REDCap の設計および構文パターンに密接に従うように設計されています。すべての REDCap API メソッドは、特定の必須パラメータを提供し、ユーザー入力の有効性をチェックする関数として利用可能です。

戻り値と REDCap メッセージは、直接文字列として返されますが、ドキュメントではこれらを有用な方法で解析する方法が示されています。

関数引数は、REDCap メソッドパラメータにちなんで名付けられています。これらは名前付き引数として渡され、直感的な型の値を取ります。

### `token` と `url`

ほとんどすべての REDCap メソッドは、プロジェクトとユーザーに固有のトークンを受け入れます。

URL はこの例と正確に一致する必要があります： `https://example.example/redcap/api/`

あなたの REDCap トークンとあなたの機関の REDCap API URL は、デフォルトで Julia の環境変数から読み取ることができます。次の行を [あなたのローカル Julia スタートアップファイル](https://docs.julialang.org/en/v1/manual/command-line-interface/#Startup-file)（おそらく `~/.julia/config/startup.jl`）に追加することで、REDCap.jl に利用可能にすることができます：

```julia
ENV["REDCAP_API_TOKEN"] = "C0FFEEC0AC0AC0DEC0FFEEC0AC0AC0DE"
ENV["REDCAP_API_URL"] = "http://example.com/redcap/api/"
```

これらは通常の名前付き引数として渡すこともできます。

いくつかのメソッドは、プロジェクトとプロジェクトレベルのトークンを生成するために使用できるスーパートークンを受け入れます。スーパートークンを持っている場合は、スタートアップファイルにそれを保持し、必要に応じてプロジェクトレベルのトークンを生成および保存することをお勧めします。

### `data`

`data` パラメータには、REDCap メソッドによって異なる属性のリストが含まれています。確定的な属性リストについては、公式の REDCap ドキュメントを参照してください。REDCap.jl では、これを NamedTuple（または任意の派生型）、ファイルハンドル、または文字列として指定できます。NamedTuple を使用する場合、内部的に使用する `format`（デフォルトは xml）に変換されます。

```julia
import_project_info(
    data=(
        project_title="New name",
        project_notes="New notes"
    ),
    returnFormat=:csv,
)
```

ただし、1つの値を持つ NamedTuple にはカンマが必要であることに注意してください：

```julia
import_project_info(
    data=(
        project_title="New name", # このカンマは必須です
    ),
    returnFormat=:csv,
)
```

`Dict` 値も問題ありません。

```julia
import_project_info(data=Dict(:project_title=>"New name"), returnFormat=:csv)
```

文字列値も受け入れられます。文字列がファイル名である場合、そのファイルの内容が送信されます。それ以外の場合、値は API リクエストの一部として直接送信されます。

```julia
data_string = """
    [{"data_access_group_name":"CA Site","unique_group_name":"ca_site"},
    {"data_access_group_name":"FL Site","unique_group_name":"fl_site"},
    {"data_access_group_name":"New Site","unique_group_name":""}]
"""
out = open("data_file.json","w"); write(out, data_string); close(out)

import_DAGs(token=t,data=data_string, format=:json) # 文字列が API に渡されます

import_DAGs(token=t, data="data_file.json", format=:json) # 文字列がファイル名としてパターンマッチされます
```

コレクションについては、現在スカラーエントリのコレクションのみがサポートされています。したがって、属性と値のリストは受け入れられますが、列ごとに複数の行を含む Dict はファイルからのみ読み取ることができます。

REDCap API では、`data` パラメータの存在がメソッドの動作を変更することがよくあります。たとえば、ほとんどのインポートメソッドは、データパラメータが追加されたエクスポートメソッドとして実装されています。REDCap.jl では、`import_project_data` が `export_project_data` として動作することはバグと見なされるため、データパラメータは存在する場合ほぼ常に必要です。

### `format` と `returnFormat`

サポートされているオプションは `:csv`、`:json`、`:xml`（デフォルト値）、および時々 `:odm` です。これらの値は文字列またはシンボルとして渡すことができます。

インポートメソッドの場合、`format` パラメータはユーザー入力を指定し、`returnFormat` パラメータは REDCap メッセージと戻り値に適用されます。それ以外の場合、REDCap メッセージと戻り値に適用される単一の `format` パラメータのみが一般的です。

### `content` と `action`

`content` と `action` パラメータは、ほとんどの REDCap メソッドを定義するものです。REDCap.jl では、これらは内部で渡され、ユーザーが提供する必要はありません。代わりに、各関数に対して固定されています。

## トラブルシューティング

  * 関数呼び出しが期待される結果を生成しない場合は、`ENV["JULIA_DEBUG"] = REDCap` を実行して、このパッケージのデバッグメッセージを表示してみてください。
  * `data` パラメータはフォーマットされた文字列に変換されるため、異なるフォーマットパラメータ（`:csv`、`:json`、または `:xml`）を試してみてください。

入力データパラメータのフォーマットが不明な場合は、ブラウザで例を設定し、データをエクスポートしてみてください。インポートする前に、特定の生成された列の値を削除する必要があるかもしれません。

  * 予期しないエラーや機能リクエストについては、自由に問題を作成してください。
