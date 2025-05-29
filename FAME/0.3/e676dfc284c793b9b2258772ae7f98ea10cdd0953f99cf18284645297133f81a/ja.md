```
opendb(dbname, [mode])
```

FAMEデータベースを開き、そのインスタンスを[`FameDatabase`](@ref)として返します。

`dbname`は、.dbファイルへのパスまたは、以下の形式でリモート接続を指定する文字列です。

```
"[<tcp_port>@]<host> [<username> [<password>] ] <db>"
```

`mode`は整数（CHLIヘルプを参照）または`Symbol`です。有効なモードには`:readonly`、`:create`、`:overwrite`、`:update`、`:shared`、`:write`、`:direct_write`が含まれます。
