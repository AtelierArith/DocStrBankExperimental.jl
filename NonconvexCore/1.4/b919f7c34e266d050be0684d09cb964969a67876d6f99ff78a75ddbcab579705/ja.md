```
IpoptCriteria
```

この収束基準は、収束を評価するためにスケーリングされたカラッシュ-クーン-タッカー（KKT）残差と最大不適合性を使用します。このスケーリングされたKKT残差は、[この論文](http://cepac.cheme.cmu.edu/pasilectures/biegler/ipopt.pdf)で説明されているように、IPOPT非線形プログラミングソルバーで使用されます。詳細は[`assess_convergence!`](@ref)に記載されています。
