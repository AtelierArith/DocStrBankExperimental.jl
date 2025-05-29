```
@authenticate!(exception::E = ExceptionalResponse(Genie.Renderer.redirect(:show_login)))
```

If the current request is not authenticated it throws an ExceptionalResponse exception.
