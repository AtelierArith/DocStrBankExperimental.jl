```
macro threaded_loop(code)
```

条件付きスレッドループ `Threads.@threads` による。`using_threaded_loop()` が true を返す場合、並列ループを実行し、それ以外の場合は直列ループを実行します。

注意: 並列ループが実行されている場合、ループ本体内の他のすべての並列化形式はオフになります。

#### 例:

```
@threaded_loop for i = 1 : N
    # 並列で処理を行う
end
```
