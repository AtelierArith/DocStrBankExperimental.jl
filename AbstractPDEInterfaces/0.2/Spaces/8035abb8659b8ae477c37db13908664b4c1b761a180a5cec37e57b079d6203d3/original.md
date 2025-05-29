(v,-∇² u) = (vx,ux) + (vy,uy)

```
     := a(v,u)

      = v' * A * u

      = (Q*R'*v)'*A_l*(Q*R'*u)

      = v'*R*Q'*A_l*Q*R'*u
```

implemented as

R'R * QQ' * A*l * u*loc where A_l is

[Dr]'*[rx sx]'*[B 0]*[rx sx]*[Dr] [Ds]  [ry sy]  [0 B] [ry sy] [Ds]

= [Dr]' * [G11 G12]' * [Dr]   [Ds]    [G12 G22]    [Ds]
