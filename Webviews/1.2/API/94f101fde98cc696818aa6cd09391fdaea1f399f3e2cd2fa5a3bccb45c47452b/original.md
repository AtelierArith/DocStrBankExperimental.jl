```
eval!(w::Webview, js::AbstractString)
```

Evaluates arbitrary JavaScript code. Evaluation happens asynchronously, also the result of the expression is ignored. Use `bind` if you want to receive notifications about the results of the evaluation.
