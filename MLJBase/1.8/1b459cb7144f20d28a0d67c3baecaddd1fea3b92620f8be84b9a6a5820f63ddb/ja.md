```
last_model(mach::Machine)
```

マシン `mach` をトレーニングするために使用された最後のモデルを返します。これは、`mach.model` がシンボルであっても、正真正銘のモデルです。

`mach` がトレーニングされていない場合は `nothing` を返します。
