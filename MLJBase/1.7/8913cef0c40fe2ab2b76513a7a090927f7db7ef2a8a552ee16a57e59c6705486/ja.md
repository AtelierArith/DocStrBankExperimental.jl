```
restore!(mach::Machine)
```

現在シリアライズ可能であるが、他の方法では使用できない可能性のあるマシンの状態を復元します。そのようなマシン `mach` に対しては、`mach.state=1` となります。デシリアライズされたマシンオブジェクトを使用可能な形式に復元するために意図されています。

例については [`serializable`](@ref) を参照してください。
