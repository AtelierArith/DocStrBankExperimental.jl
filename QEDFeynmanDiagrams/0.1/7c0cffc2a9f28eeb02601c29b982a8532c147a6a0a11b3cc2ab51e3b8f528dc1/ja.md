```
number_of_diagrams(proc::AbstractProcessDefinition)
```

与えられた [`QEDbase.AbstractProcessDefinition`](@extref) に対して、ツリー レベルでの有効なファインマン ダイアグラムの数を返します。これは次の式に相当します。

$$
\frac{(M + 3N - 3)!}{(2N - 1)!} * E! * U! * T!
$$

ここで、 $M \dots$ 外部光子の数、 $E \dots$ 電子線の数、 $U \dots$ ミュー線の数、 $T \dots$ タウ線の数、そして $N = E + U + T$ です。 電子/ミュー/タウの「線」は、入ってくるフェルミオンと出てくる反フェルミオンのペア、またはその逆です。
