```
print_devices()
```

利用可能なデバイスを印刷するシンプルな関数です。内部の get_backend() 関数を呼び出して適切な GPU / CPU バックエンドを取得し、デバイス情報を印刷します。

# 引数

  * 'use_gpu':  ('::Bool') 真の場合、読み込まれた / 機能する GPU バックエンドを確認し、GPU バックエンドが読み込まれていない場合は適切な警告を印刷します。
