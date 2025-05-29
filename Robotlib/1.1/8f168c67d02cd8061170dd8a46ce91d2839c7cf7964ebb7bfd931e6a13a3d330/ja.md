```
Tn0, xi, et, er = calibLPOE(xin, Tn0in, Ta, q; maxiter=10, λ=1.0)
```

ローカルPOEの運動学の定式化を使用して運動学的キャリブレーションを実行します。

  * `Tn0` 名目上の前方運動学
  * `xi` ツイスト
  * `et` アルゴリズムの反復の関数としての平行誤差
  * `er` アルゴリズムの反復の関数としての回転誤差
  * `λ` 正則化パラメータ

シミュレーションされた使用法については `runtests.jl` を参照してください。キャリブレーション目的のためのシミュレーションデータを生成するいくつかの関数は /home/terasaki/.julia/packages/Robotlib/Cqg2z/src/calibLPOE.jl に提供されています。
