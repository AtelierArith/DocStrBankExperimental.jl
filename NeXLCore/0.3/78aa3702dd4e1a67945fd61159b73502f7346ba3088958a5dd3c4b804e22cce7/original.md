```
n"Fe"
```

Implements compile time parsing of strings to produce Element, SubShell, AtomicSubShell, Transition or CharXRay objects.  The only oddity is that to get SubShell("K") you must enter n"K1" to differentiate the sub-shell from potassium. Examples:

```
n"Fe" == elements[26]
n"K" == elements[19]
n"K1" == subshell("K")
n"L3" == subshell("L3")
n"Fe L3" == AtomicSubShell(elements[26],subshell("L3"))
n"L3-M5" == Transition(SubShell("L3"),"SubShell("M5"))
n"Fe L3-M5" == CharXRay(elements[26],Transition(SubShell("L3"),"SubShell("M5"))
```
