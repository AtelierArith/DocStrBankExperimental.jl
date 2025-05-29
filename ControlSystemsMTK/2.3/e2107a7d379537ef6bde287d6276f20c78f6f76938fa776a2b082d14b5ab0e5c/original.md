```
G = ControlSystemsBase.feedback(loopgain::T; name)
```

Form the feedback-interconnection $G = L/(1+L)$

The system `G` will be a new system with `input` and `output` connectors.
