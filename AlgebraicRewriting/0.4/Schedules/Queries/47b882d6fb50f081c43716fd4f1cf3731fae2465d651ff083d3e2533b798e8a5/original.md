Has an A input/output and a B input/output (by default, the B input can be  changed to some other type if needed). 

```
A  R ---------↖
↓  ↓          []
```

⌜–––-⌝       []   | Query | [agent subroutine]    ⌞–––-⌟       []    ↓  ↓  ↓        []    A  B  ∅        []       ↘–––––-↗ Performs one action per element of Hom(B,X), optionally with some constraints. (i.e. sends you out along the B wire with agent Bₙ->X). 

After you have done this for all Bₙ, then you exit the A port (you need to  update the A->X map, and, if at any point the agent was deleted, then you exit a  third door typed by 0).

A constraint optionally will be applied to (1) the A->W<-B cospan of old agent  and purported new agent. (the new agent is the first argument to the constraint) 
