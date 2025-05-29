function initiate(p::Project)

This is the main function compose all other function together and upon giving value of type project function will validate the initialisers and create a new project or load a existing project.

# Argument

  * p: value of type Project

# Example

```
p = Project(
    id="xyz",
    name="My Fancy? *Project1 2 ",
    template="jl",
    profile="default"
)
initiate(p)
```
