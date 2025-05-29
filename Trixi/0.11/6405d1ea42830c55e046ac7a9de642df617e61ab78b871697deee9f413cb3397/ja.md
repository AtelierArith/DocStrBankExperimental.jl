```
semidiscretize(semi::AbstractSemidiscretization, tspan)
```

セミ離散化 `semi` を時間区間 `tspan` のODE問題としてラップし、[SciMLエコシステム](https://diffeq.sciml.ai/latest/) の `solve` に渡すことができます。
