```
Transition
```

Represents an inner and outer shell that describe an X-ray transition. Only transitions for which one or more element has a characteristic x-ray are supported according to the default line weight database (weight > 0 for one or more Z). This structure does not contain the Element information necessary to specify a characteristic X-ray.

Data items:

```
innerShell::SubShell
outerShell::SubShell
```

Example:

```
tr1 = Transition(n"K1",n"L3")
tr2   = Transition(SubShell(1),SubShell(4))
@assert tr1==tr2
```
