```
@authenticate!(exception::E = ExceptionalResponse(Genie.Renderer.redirect(:show_login)))
```

現在のリクエストが認証されていない場合、ExceptionalResponse例外をスローします。
