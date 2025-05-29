```
t8_cmesh_set_refine(cmesh, level, scheme)
```

cmeshを指定されたレベルにリファインします。したがって、各ツリーをx^levelのサブツリーに分割します TODO: 実装する

### プロトタイプ

```c
void t8_cmesh_set_refine (t8_cmesh_t cmesh, int level, t8_scheme_cxx_t *scheme);
```
