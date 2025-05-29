```
mgslist = mgs_ped(pedlist)
mgslist = mgs_ped(pedlist, males)
```

父系と母系祖父（MGS）のみを持つ系図リストを作成します。返されるリスト `mgslist` は `pedlist` と同じ次元を持ちますが、2行目には MGS コードが含まれます。`pedlist` の UPG コードは削除されます。ブールベクトル `males` はオス（`true`）またはメス（`false`）を示します。デフォルトでは、すべての動物はオスとして扱われます。
