```
rewrite_match_maps(r::Rule{:DPO}, m)
```

Apply a DPO rewrite rule (given as a span, L<-I->R) to a ACSet using a match morphism `m` which indicates where to apply the rewrite.               l   r            L <- I -> R          m ↓    ↓    ↓            G <- K -> H

This works for any type that implements `pushout_complement` and `pushout`
