```
BS = BasisSpec(dvec, dvec_loc, c2f, description)
```

は、次のフィールドを含むBasisSpecオブジェクトのデータ構造です：

  * `levlist::Vector{Tuple{Int, Int}}`: 特定の基底を指定する整数のシーケンス
  * `c2f::Bool`: true（デフォルト）の場合、これは基底が粗から細への辞書から来ていることを示します；falseの場合、これは基底が細から粗への辞書から来ていることを示します
  * `description::String`: 指定された基底の説明

Copyright 2015 The Regents of the University of California

Implemented by Jeff Irion (Adviser: Dr. Naoki Saito) | Translated to julia and revised by Naoki Saito, Feb. 22, 2017 Modified by Yiqun Shao, May. 20, 2018
