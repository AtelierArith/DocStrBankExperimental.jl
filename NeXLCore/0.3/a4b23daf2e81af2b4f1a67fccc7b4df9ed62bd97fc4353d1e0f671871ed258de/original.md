Algorithms that implement the mean ionization potential.  The mean ionization potential is the primary parameter in continuous slowing down models of electron energy loss in matter.  Electrons primarily lose energy through two mechanisms - 1) collision stopping power parameterized by J, the mean ionization potential; and 2) Bremsstrahlung production.  Two or three orders of magnitude more energy is lost to collisional loss so collisional loss dominates the process and losses due to Bremsstrahlung production are insignificant relative to the uncertainty in collisional loss.

Implement this:

```
J(::Type{<:NeXLMeanIonizationPotential}, z)  # in eV
```

Also provided:

```
J(::Type{<:NeXLMeanIonizationPotential}, elm::Element)  # in eV
```
