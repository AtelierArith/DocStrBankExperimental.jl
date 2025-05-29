IIA <: Criterion

An object representing the independence of irrelevant alternatives IIA criterion.  According to the IIA criterion, the winner of an election should not depend on the presence or absence of less prefered candidates. Although there are several variations in the implimentation of IIA, RankChoiceVoting.jl tests for violations of IIA by removing subsets of lossing candidates.
