```
addr(a::Actor)
```

アクターのアドレスを返します。

生成されたアクターでこれを呼び出すと、そのアドレスが取得できます。アクターが生成されていない場合は `UndefRefError` がスローされます。
