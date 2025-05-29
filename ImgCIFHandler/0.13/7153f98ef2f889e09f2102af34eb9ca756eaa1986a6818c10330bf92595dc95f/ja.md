```
scan_frame_from_bin_id(binary_id,cif_block)
```

与えられた `binary_id` に基づいて `cif_block` の内容に従って scan*id、frame*id を返します。`cif_block` にスキャンまたはフレーム情報が含まれていない場合、(nothing,1) が返されます。逆の操作は `bin_id_from_scan_frame` です。
