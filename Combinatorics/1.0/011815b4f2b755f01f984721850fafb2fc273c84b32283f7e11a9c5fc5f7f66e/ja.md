```
character(λ::Partition, μ::Partition)
```

分割 `μ` のキャラクター $\chi^{\lambda(\mu)}$ を対称群 $S_n$ の $\lambda$ 番目の不可約表現 ("irrep") で計算します。

次のように Murnaghan-Nakayama アルゴリズムを実装します：

```
Dan Bernstein,
"The computational complexity of rules for the character table of Sn",
Journal of Symbolic Computation, vol. 37 iss. 6 (2004), pp 727-748.
doi:10.1016/j.jsc.2003.11.001
```
