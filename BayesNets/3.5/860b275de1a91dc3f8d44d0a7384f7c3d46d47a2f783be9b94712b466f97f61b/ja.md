与えられたターゲット変数インデックスと、アルファで与えられたディリクレ事前カウントに対するベイズスコアコンポーネントを計算します。

入力:      i       - ターゲット変数のインデックス      parents - 親変数のインデックスのリスト（自己を含んではいけません）      r       - 変数インデックスによってアクセスされるインスタンシエーションカウントのリスト                r[1] は変数 1 が取ることができる離散状態の数を示します      data - 十分統計量 / カウントの行列                d[j,k] はターゲット変数が j 番目の親インスタンシエーションに対して k 番目のインスタンシエーションを取った回数を示します

出力:      ベイズスコア、Float64
