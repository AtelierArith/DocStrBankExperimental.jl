```
isnodata(array::AbstractArray, val=0)
```

配列 `array` と同じサイズのブール配列を返し、$array[i] == val$ の場合に 1（`true`）を返します。画像でのテストでは、この関数が $ind = (I.image .== 0)$ よりも 5 倍速いことが示されました。
