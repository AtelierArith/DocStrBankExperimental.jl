```
become(service, old::Actor, reincarnated::Actor)
```

`old` アクターを `new` に転生させます。つまり、`old` はスケジュールから外れ、`reincarnated` は `old` のアドレスを再利用してスケジュールされます。

`onbecome` ライフサイクルコールバックが呼び出されます。

注意: 名前が示すように、`become` は行動変化のサーコニアンの方法です。
