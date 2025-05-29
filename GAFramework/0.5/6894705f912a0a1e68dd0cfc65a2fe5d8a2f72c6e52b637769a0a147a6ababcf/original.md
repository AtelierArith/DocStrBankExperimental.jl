Logging     * saves state every save*state*iter iterations to file         - restart using state = loadgastate(filename) & ga!(state)     * outputs creature every save*creature*iter iterations to file     * prints fitness value every print*fitness*iter iterations to screen

```
print the fitness of fittest creature every n iteration
    print_fitness_iter::Int
save the fittest creature to file every n iteration
    save_creature_iter::Int
save the entire state of the GA (i.e. this struct) to file every n iteration
    save_state_iter::Int
prefix for the files to be save
    file_name_prefix::AbstractString
```
