vanishes*at(p, c) これは、擬似多項式 p が x=binary*vector_form(c) でゼロに評価されるかどうかをチェックします。この長い実装は速度とメモリの最適化のために最適化されています。さもなければ、単に return !(isempty(intersect(p.y,c))) || !(issubset(p.x,c)) とすることができたでしょう。
