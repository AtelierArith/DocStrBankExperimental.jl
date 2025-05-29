Creates Ohms constraints (yt post fix indicates that Y and T values are in rectangular form) for damaged lines

```
p_fr ==    he * g[c,c] * vm_fr[c]^2 +
            sum( g[c,d]*vm_fr[c]*vm_fr[d]*cos(va_fr[c]-va_fr[d]) +
                 b[c,d]*vm_fr[c]*vm_fr[d]*sin(va_fr[c]-va_fr[d]) for d in conductor_ids(pm) if d != c) +
            sum(-g[c,d]*vm_fr[c]*vm_to[d]*cos(va_fr[c]-va_to[d]) +
                -b[c,d]*vm_fr[c]*vm_to[d]*sin(va_fr[c]-va_to[d]) for d in conductor_ids(pm))
            + g_fr[c,c] * vm_fr[c]^2 +
            sum( g_fr[c,d]*vm_fr[c]*vm_fr[d]*cos(va_fr[c]-va_fr[d]) +
                 b_fr[c,d]*vm_fr[c]*vm_fr[d]*sin(va_fr[c]-va_fr[d]) for d in conductor_ids(pm) if d != c)
            )
q_fr == he * -b[c,c] *vm_fr[c]^2 -
            sum( b[c,d]*vm_fr[c]*vm_fr[d]*cos(va_fr[c]-va_fr[d]) -
                 g[c,d]*vm_fr[c]*vm_fr[d]*sin(va_fr[c]-va_fr[d]) for d in conductor_ids(pm) if d != c) -
            sum(-b[c,d]*vm_fr[c]*vm_to[d]*cos(va_fr[c]-va_to[d]) +
                 g[c,d]*vm_fr[c]*vm_to[d]*sin(va_fr[c]-va_to[d]) for d in conductor_ids(pm))
            -b_fr[c,c] *vm_fr[c]^2 -
            sum( b_fr[c,d]*vm_fr[c]*vm_fr[d]*cos(va_fr[c]-va_fr[d]) -
                 g_fr[c,d]*vm_fr[c]*vm_fr[d]*sin(va_fr[c]-va_fr[d]) for d in conductor_ids(pm) if d != c)
            )
```
