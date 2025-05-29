```
connect_remote([host=localhost,] port::Integer=27754;
             tunnel = (host != localhost) ? :ssh : :none,
             ssh_opts = ``, session_id = nothing)
```

リモートサーバーにREPL統合なしで接続します。これにより、REPLモードではなく`@remote`を使用できます。REPLが利用できないが、JupyterやPlutoノートブックのように対話性が求められる状況で便利です。それ以外の場合は、`connect_repl`を参照してください。
