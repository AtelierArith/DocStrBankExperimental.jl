```
filter!(psum::PauliSum, filterfunc::Function)
```

`filterfunc`を満たすすべてのパウリ文字列を削除することによって、`PauliSum`をインプレースでフィルタリングします。
