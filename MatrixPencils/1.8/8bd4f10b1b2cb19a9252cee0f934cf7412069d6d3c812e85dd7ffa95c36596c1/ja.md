```
 lsbalance!(A, B, C; withB = true, withC = true, maxred = 16) -> D
```

システム行列の1ノルムを減少させます 

```
         S =  ( A  B )
              ( C  0 )
```

標準システムトリプル `(A,B,C)` に対応するバランスを取ることによって。これは、行と列をできるだけノルムが近くなるようにするために、対角類似変換 `inv(D)*A*D` を含みます。

次の特定のシステム行列に対して、バランスをオプションで実行できます:   

```
    S = A, if withB = false and withC = false ,
    S = ( A  B ), if withC = false,     or    
    S = ( A ), if withB = false .
        ( C )
```

キーワード引数 `maxred = s` は、ゼロ行または列が存在する場合に、`S` の1ノルムの最大許容減少を指定します（イテレーション内で）。 `s` は正の2の累乗でなければならず、そうでない場合は `s` は最も近い2の累乗に丸められます。   

*注:* この関数は、LAPACKファミリー `*GEBAL.f` の拡張を表すSLICOTルーチン `TB01ID.f` の翻訳です。また、[1]で提案された修正も含まれています。

[1]  R.James, J.Langou and B.Lowery. "On matrix balancing and eigenvector computation."      ArXiv, 2014, http://arxiv.org/abs/1401.5766
