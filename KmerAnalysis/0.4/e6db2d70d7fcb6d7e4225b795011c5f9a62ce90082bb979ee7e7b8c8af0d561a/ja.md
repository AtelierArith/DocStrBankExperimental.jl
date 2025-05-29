```
add_count!(mc::IndexedCounts{M}, name::Symbol, reads::ReadDatastore) where {M}
```

ReadDatastore内のk-merをカウントし、それをIndexedCounts{M}に追加します。

現在、IndexedCountsはシリアルでメモリ内のカウント方法を使用しています、次のように

!!! note
    IndexedCountsのインデックスにあるk-merのみがリードからカウントされます。

