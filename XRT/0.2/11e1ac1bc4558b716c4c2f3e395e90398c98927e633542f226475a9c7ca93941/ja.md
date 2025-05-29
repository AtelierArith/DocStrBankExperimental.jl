```julia
wait(run::XRT.XRTWrap.Run) -> XRT.XRTWrap.ErtCmdState.Type

```

指定された [`Run`](@ref) オブジェクトが実行を完了するのを待ちます。このメソッドは、実行が完了するとすぐに戻ります。
