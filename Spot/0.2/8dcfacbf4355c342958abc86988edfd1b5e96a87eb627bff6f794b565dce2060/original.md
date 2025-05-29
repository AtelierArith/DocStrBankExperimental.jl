```
LTLTranslator
```

Translates a Linear Temporal Logic formula to an automata 

# Fields

  * tgba::Bool = true  outputs Transition-based Generalized Büchi Automata
  * buchi::Bool = false outputs state-based Büchi automata
  * monitor::Bool = false outputs monitors
  * deterministic::Bool = true combined with generic, will do whatever it takes to produce a deterministic automaton, and may use any acceptance condition
  * generic::Bool = true
  * parity::Bool = true combined with deterministic, will produce a deterministic automaton with parity acceptance
  * state*based*acceptance::Bool = true define the acceptance using states
