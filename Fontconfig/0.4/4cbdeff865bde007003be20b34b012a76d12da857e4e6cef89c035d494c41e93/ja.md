```
list(pat::Pattern=Pattern(), properties = ["family", "style", "file"])::Vector{Pattern}
```

`pat`に一致するフォントを選択し、それらのフォントからパターンを作成します。これらのパターンは`properties`にリストされたプロパティのみを含み、ユニークなそのようなパターンのベクターを`Vector{Pattern}`として返します。
