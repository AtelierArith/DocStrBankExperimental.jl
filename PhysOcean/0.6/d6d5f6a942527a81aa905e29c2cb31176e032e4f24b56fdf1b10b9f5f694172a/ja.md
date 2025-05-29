fdeep = deepestpoint(mask,f,dim=ndims(f));

# 入力:

  * mask: 考慮すべきポイントに対してtrue。
  * f: ポイントが取得される配列
  * dim: 深さが見つかり、積分が行われる次元。指定されていない場合は最後の次元が使用されます。

# 出力:

  * maskでfalseでない最高インデックスにあるdim方向のfの値

# 注意:
