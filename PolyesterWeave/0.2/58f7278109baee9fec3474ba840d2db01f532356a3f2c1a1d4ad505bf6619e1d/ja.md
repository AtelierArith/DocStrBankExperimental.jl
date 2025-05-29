`request_threads` は、実行するための `ThreadingUtilities` ワーカータスクのセットを要求するために呼び出されます。

```
julia> using PolyesterWeave

julia> PolyesterWeave.request_threads(12)
((Thread (12) Iterator: U[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12],), (0x0000000000000fff,))
```

これは、利用可能なスレッド 1-12 `U[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]` に対するイテレータと、作業が完了したときにこれらのスレッドを解放するために使用する必要があるマスクを返します。

要求を行うスレッドは常に作業の一部を行う必要があることに注意してください。したがって、13 スレッドで実行したい場合は、12 を要求します。8 スレッドで実行したい場合は、7 を要求します。など。

システムで利用可能なスレッドよりも多くを要求すると、利用可能なものだけが得られます：

```
julia> Sys.CPU_THREADS, Threads.nthreads()
(16, 8)

julia> r1 = PolyesterWeave.request_threads(30) # 注意: 8 ではなく 7 しか得られません
((Thread (7) Iterator: U[1, 2, 3, 4, 5, 6, 7],), (0x000000000000007f,))

julia> r2 = PolyesterWeave.request_threads(30)
((Thread (0) Iterator: UInt64[],), (0x0000000000000000,))
```

以下は、いつでも削除される可能性のあるサポートされていない機能です：

要求中に、取得できるスレッドをマスクすることもできます。たとえば、この呼び出し：

```
julia> Sys.CPU_THREADS, Threads.nthreads()
(96, 96)

julia> r1 = PolyesterWeave.request_threads(96, 0xa)
((Thread (2) Iterator: U[2, 4], Thread (31) Iterator: U[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31]), (0x000000000000000a, 0x000000007fffffff))
```

は、96 スレッドを要求していますが、マスク `0x0a` により最初の 64 のスレッドのうち 2 と 4 以外が無効になります：

```
julia> bitstring(0xa)
"00001010"
```

したがって、イテレータ `U[2,4]` と、次の 64 のバッチからのすべての利用可能な作業に対するイテレータが得られました。
