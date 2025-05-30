```
t8_offset_next_nonempty_rank(rank, mpisize, offset)
```

次の空でない高いランクを見つけます。このランクが存在しない場合はmpisizeを返します。

# 引数

  * `proc`:[in] MPIランク。
  * `mpisize`:[in] 総MPIランクの数。
  * `offset`:[in] 少なくとも*mpisize* + 1のエントリを持つ配列。

# 戻り値

ランク*p*を返します。ここで*p* > *rank* かつ [`t8_offset_empty`](@ref) (*p*, *offset*) がTrueであり、かつ[`t8_offset_empty`](@ref) (*q*, *offset*) がFalseであるすべての*rank* < *q* < *p*に対してです。このような*q*が存在しない場合は*mpisize*が返されます。

### プロトタイプ

```c
int t8_offset_next_nonempty_rank (const int rank, const int mpisize, const t8_gloidx_t *offset);
```
