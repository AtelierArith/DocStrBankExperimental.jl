```
load_model
```

HuggingFaceから論文で提示されたモデルをロードします。`load_head`が`true`の場合、モデルは分類のためにヘッド（すなわち最終層）付きでロードされます。`load_head`が`false`の場合、モデルはヘッドなしでロードされます。後者は、異なるタスクに対してモデルをファインチューニングする場合や、分類ヘッドが必要ない場合に便利です。`Transformers.HuggingFace.HGFConfig`が受け入れる任意の追加キーワード引数を受け付けます。
