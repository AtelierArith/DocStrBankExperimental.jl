```
sink!(array,x;[samplerate],[offset])
```

信号 `x` の `size(array,1)` サンプルを `array` に書き込みます。`offset` の後のサンプルから始まります。`x` に対してサンプルレートが指定されていない場合は、`samplerate` を使用して今指定できます（デフォルトは44.1kHzです）。
