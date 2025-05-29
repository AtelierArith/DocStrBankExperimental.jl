```
orthogonal(X::AbstractMatrix{<:Real})
```

直交行列に制約された`value`を持つパラメータを生成します。引数`X`は直交である必要はありません。

この機能は、`X`を直交行列の最近接要素部分空間に投影します（フロベニウスノルムにおいて）およびその結果として過剰パラメータ化されています。

元々はvarzで使用されていました: https://github.com/wesselb/varz/blob/master/varz/vars.py#L446
