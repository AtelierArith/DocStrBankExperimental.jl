```
neighbours(geohash, bits_per_char = 2)
```

指定されたgeohashセルの隣接するセルのgeohashを計算します。"north"、"north-east"、"east"などのキーを持つ辞書を返し、対応する隣接セルのgeohash文字列を同じ精度と文字あたりのビット数で値として持ちます。極に近いセルは隣接するセルが5つしかないことに注意してください。
