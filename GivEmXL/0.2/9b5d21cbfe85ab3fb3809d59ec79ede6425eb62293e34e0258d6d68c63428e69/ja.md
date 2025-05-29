```
complete_interact(pp0, pps, proc_data_fn::Function; kwargs...) → nothing
complete_interact(pp0, pps, proc_data_fns::Tuple; kwargs...) → nothing
```

これはユーザーとのインタラクションを構築するためのトップレベル関数です。詳細についてはドキュメントのフローダイアグラムを参照してください。最初に[`proc_ARGS`](@ref)を呼び出し、次に[`prompt_and_parse`](@ref)を複数回呼び出し、ユーザーがGUIを使ってファイルを選択できるようにします。入力はExcelファイルのパラメータとマージされ、すべてがユーザー提供の関数に渡されてデータ処理が行われます。

# 引数

  * `pp0::Union{Nothing, ArgumentParser}`: コマンドライン引数用のArgumentParser。
  * `pps::NamedTuple`: 個別のダイアログ用のArgumentParsers。対応するキーは `[:gen_options, :spec_options, :exelfile_prompt, :datafiles_prompt, :next_file]` です。ダイアログをスキップするには、キーをスキップしてください。
  * `proc_data_fn(; xlfile, datafiles, paramsets)::Function`: 実際のデータ処理を行う関数です。これらの3つのキーワード引数を取ります。
  * `proc_data_fns::Tuple`: 代わりに、3つの関数のタプルを提供できます：前処理、サブセットの処理、後処理。[`proc_data`](@ref)も参照してください。

# キーワード引数

  * `basedir=nothing`: ファイル選択ダイアログのベースディレクトリ。`basedir`が提供されていない場合、キャッシュされた値が使用されます。
  * `paramtables = (;setup="params_setup", exper="params_experiment")`: 対応するパラメータを含むテーブルの名前。テーブルを`nothing`に設定するとスキップされます。
  * `getexel=false`: trueの場合、Excelファイル選択ダイアログを実行します。
  * `getdata=(; dialogtype = :none)`: `:none`の場合、データファイル選択ダイアログは表示されません。それ以外の場合、パラメータは[`get_data`](@ref)関数に渡され、ファイル/ディレクトリ選択ダイアログが実行されます。

関数`complete_interact`はエクスポートされています。
