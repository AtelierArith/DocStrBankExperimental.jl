```
semidiscretize(semi::Semidiscretization, tspan)
```

セミ離散化 `semi` を、[SciMLエコシステム](https://diffeq.sciml.ai/latest/) の `solve` に渡すことができる時間区間 `tspan` のODE問題としてラップします。
