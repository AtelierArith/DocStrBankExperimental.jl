```
Command(name, parameters, arguments, subcommands)
```

実行されるコマンドを、関連するフラグ、オプション、引数、およびサブコマンドと共に表します。

# 引数

  * `name::String`: コマンドの名前。
  * `parameters`: フラグとオプションのイテラブル。
  * `arguments::Vector{String}`: コマンドへの任意の引数。
  * `subcommands::Vector{AbstractCommand}`: メインコマンドと共に実行される任意のサブコマンド。
