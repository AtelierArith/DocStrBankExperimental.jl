```
ssh=stericheight(rhoi,z,zlevel,dim::Integer=ndims(rhoi))
```

# 入力:

  * `rhoi`: 統合密度異常 (integraterhoprime の呼び出しから)
  * `z`: 垂直位置の配列
  * `zlevel`: 動きがないと仮定される zlevel の整数
  * `dim`: 深さが見つかる次元。指定されていない場合は最後の次元が使用される

# 出力:

  * `ssh`: ステリック高さ。rhoi と同じ空間次元で、dim が取り除かれる方向

現在提供されている深さレベルに対して、深さではなくインデックスとしてステリック高さを計算します。
