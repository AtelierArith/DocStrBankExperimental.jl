```
rampoff(x,[len=10ms],[fn=x -> sinpi(0.5x)])
```

信号のオフセットを段階的に変化させ、`len`秒の間にフル振幅から0振幅にスムーズに遷移します。

この関数は単調増加であり、定義域と値域は[0,1]です。

`len`と`fn`はオプションの引数です：どちらか一方または両方を指定できますが、`len`が存在する場合は`fn`の前に置かなければなりません。
