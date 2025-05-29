```
alloc(device, bytesize, [ptr=nothing];
      storage=Default, hazard_tracking=Default, cache_mode=Default)
```

`device`上に`bytesize`バイトのMetalバッファを割り当てます。最後の引数としてCPUポインタが渡された場合、バッファは`ptr`から始まるメモリの内容で初期化されます。そうでない場合はゼロ初期化されます。

! 注意: 返されたバッファを解放する責任があります

`storage`キーワード引数は、バッファがどこに保存されるかを制御します。可能な値は次のとおりです。

  * PrivateStorage : デバイス上に存在
  * SharedStorage  : ホスト上に存在
  * ManagedStorage : デバイスとホストの両方にバッファの2つのコピーを保持します。2つを同期させるためには明示的な呼び出しが必要です
  * Memoryless : iOS特有のもので、Macでは動作しません。

`PrivateStorage`バッファはCPUから直接アクセスできないため、メモリを初期化するためにポインタを渡す場合はこのオプションを使用できません。
