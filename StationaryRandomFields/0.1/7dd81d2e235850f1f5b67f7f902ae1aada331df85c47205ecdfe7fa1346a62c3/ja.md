```
generate_gaussian_noise(data::AbstractNoiseSignal; rng=Random.default_rng())
```

フーリエ空間での複素ガウスノイズを生成します。これは、信号領域でのゼロ平均と`sizeof(data)`の分散を持つ実相関のないガウスノイズのフーリエ領域表現と一致する複素配列を返します。出力配列のサイズは`rfftsize(data)`によって与えられます。
