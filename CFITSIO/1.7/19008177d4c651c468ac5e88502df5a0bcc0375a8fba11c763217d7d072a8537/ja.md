```
fits_get_hdrspace(f::FITSFile) -> (keysexist, morekeys)
```

既存のキーワードの数（ENDキーワードはカウントしない）と、さらにキーワードを追加するために現在利用可能なスペースの量を返します。
