```
debug(sess::PyObject, o::PyObject)
```

セッションの実行がTensorFlowバックエンドからエラーを返す場合、この関数は正確なエラーを印刷するのに役立ちます。たとえば、詳細なエラー情報がない `InvalidArgumentError()` に遭遇することがあり、この関数はデバッグに役立ちます。
