LPACコールドスタートAC電力フロー近似。

LPACコールドスタートモデルは、最も少ない情報を必要としますが、LPACモデルの中で最も精度が低いバリアントでもあります。名目上のAC動作点が利用可能な場合、LPACウォームスタートモデルは精度を向上させます。

元の出版物では、コサインおよび線形熱制約のために多面体外近似を使用することが提案されています。最近のMIQCQPソルバーの改善を考慮して、この実装ではそれらの制約に二次関数を使用しています。

```
@article{doi:10.1287/ijoc.2014.0594,
  author = {Coffrin, Carleton and Van Hentenryck, Pascal},
  title = {A Linear-Programming Approximation of AC Power Flows},
  journal = {INFORMS Journal on Computing},
  volume = {26},
  number = {4},
  pages = {718-734},
  year = {2014},
  doi = {10.1287/ijoc.2014.0594},
  eprint = {https://doi.org/10.1287/ijoc.2014.0594}
}
```
