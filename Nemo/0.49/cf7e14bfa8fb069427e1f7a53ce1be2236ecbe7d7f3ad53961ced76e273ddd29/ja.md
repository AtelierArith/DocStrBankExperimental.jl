```
rand(R::QQBarField; degree::Int, bits::Int, randtype::Symbol=:null)
```

次数が `degree` までのランダム代数数を返し、係数は `bits` のサイズまでです。デフォルトでは、実数と複素数の両方が生成されます。オプションの `randtype` を `:real` または `:nonreal` に設定すると、特定のタイプの数を生成します。非実数は少なくとも `degree` が 2 である必要があることに注意してください。
