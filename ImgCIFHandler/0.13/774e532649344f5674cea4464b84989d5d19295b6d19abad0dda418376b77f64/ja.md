```
get_beam_centre(filename,scan,frame)
```

`scan`内の`frame`のビーム中心を返します。すべての軸位置を考慮に入れます。`det_data`はハンドルが破棄されるまで保持される必要があるため、返します。座標の順序は遅い方向、速い方向です。
