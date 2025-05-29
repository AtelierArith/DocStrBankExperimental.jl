```
run_git_directory(start_dir::String="."; export_options...)
```

[`run_directory`](@ref)と同様ですが、`start_dir`で自動的に`git pull`を実行し、ディレクトリの変更に合わせてスライダーサーバーを更新します。詳細についてはREADMEをご覧ください。

`PlutoDeployment.toml`ファイルを使用している場合、このファイルが変更されたかどうかも定期的にチェックします。変更された場合、**Juliaセッションを終了**し、再起動する必要があります。これが問題であれば、問題を報告してください。
