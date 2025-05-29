```
n"Fe"
```

文字列のコンパイル時解析を実装して、Element、SubShell、AtomicSubShell、Transition、またはCharXRayオブジェクトを生成します。唯一の奇妙な点は、SubShell("K")を取得するには、カリウムと区別するためにn"K1"と入力する必要があることです。例:

```
n"Fe" == elements[26]
n"K" == elements[19]
n"K1" == subshell("K")
n"L3" == subshell("L3")
n"Fe L3" == AtomicSubShell(elements[26],subshell("L3"))
n"L3-M5" == Transition(SubShell("L3"),"SubShell("M5"))
n"Fe L3-M5" == CharXRay(elements[26],Transition(SubShell("L3"),"SubShell("M5"))
```
