```
semidiscretize(semi::AbstractSemidiscretization, tspan, 
               restart_file::AbstractString)
```

セミ離散化 `semi` を時間区間 `tspan` のODE問題としてラップし、[SciMLエコシステム](https://diffeq.sciml.ai/latest/) の `solve` に渡すことができます。初期条件などは `restart_file` から取得されます。
