```Julia
wait(interrupt::XRT.XRTWrap.IPInterrupt)
wait(interrupt::XRT.XRTWrap.IPInterrupt, timeout::Integer) -> XRT.XRTWrap.CVStatus.Type

```

IPからの割り込みを待機するか、指定されたタイムアウトが切れるのを待ちます。
