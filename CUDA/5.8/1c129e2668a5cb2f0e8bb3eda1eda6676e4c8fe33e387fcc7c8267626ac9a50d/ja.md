```
update(exec::CuGraphExec, graph::CuGraph; [throw_error::Bool=true])
```

実行可能なグラフがグラフで更新できるかどうかを確認し、可能であれば更新を実行します。更新が成功したかどうかを示すブール値を返します。`throw_error`がfalseに設定されていない限り、更新が失敗した場合はエラーもスローします。
