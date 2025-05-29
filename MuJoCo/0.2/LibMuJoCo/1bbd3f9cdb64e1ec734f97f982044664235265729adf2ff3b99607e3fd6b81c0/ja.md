```
mjr_blitBuffer(src, dst, flg_color, flg_depth, con)
```

現在のフレームバッファのsrcビューポイントから、他のフレームバッファのdstビューポイントにブリットします。srcとdstのサイズが異なり、flg*depth==0の場合、色はGL*LINEARで補間されます。
