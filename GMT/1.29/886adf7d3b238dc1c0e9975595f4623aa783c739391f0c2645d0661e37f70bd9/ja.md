```
image_cpt!(img::GMTimage, cpt::GMTcpt, clear=false)
```

または

```
image_cpt!(img::GMTimage, cpt::String, clear=false)
```

cptの色からGMTimageオブジェクトにカラーマップを追加（または置き換え）します。これは、IMGがインデックスされている場合にのみ効果があります。`image_cpt!(img, clear=true)`を使用して、IMGに以前存在していた`colormap`フィールドを削除します。
