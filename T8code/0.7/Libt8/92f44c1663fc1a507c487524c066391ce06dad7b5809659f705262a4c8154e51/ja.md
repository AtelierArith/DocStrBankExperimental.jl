```
t8_offset_next_nonempty_rank(rank, mpisize, offset)
```

次の空でない高いランクを見つけます。 このランクが存在しない場合は、mpisizeを返します。

# 引数

  * `proc`:[in] MPIランク。
  * `mpisize`:[in] 総MPIランクの数。
  * `offset`:[in] 少なくとも *mpisize* + 1 エントリを持つ配列。

# 戻り値

ランク *p* であり、*p* > *rank* かつ [`t8_offset_empty`](@ref) (*p*, *offset*) が True であり、かつ [`t8_offset_empty`](@ref) (*q*, *offset*) が False であるすべての *rank* < *q* < *p* に対して。 そのような *q* が存在しない場合は、*mpisize* が返されます。

### プロトタイプ

```c
int t8_offset_next_nonempty_rank (const int rank, const int mpisize, const t8_gloidx_t *offset);
```
