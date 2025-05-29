ログ     * 状態をファイルに毎 save*state*iter 回保存         - state = loadgastate(filename) を使用して再起動 & ga!(state)     * 生物を毎 save*creature*iter 回ファイルに出力     * フィットネス値を毎 print*fitness*iter 回画面に表示

```
最もフィットな生物のフィットネスを毎 n 回のイテレーションで表示
    print_fitness_iter::Int
最もフィットな生物を毎 n 回のイテレーションでファイルに保存
    save_creature_iter::Int
GAの全状態（すなわちこの構造体）を毎 n 回のイテレーションでファイルに保存
    save_state_iter::Int
保存するファイルのプレフィックス
    file_name_prefix::AbstractString
```
