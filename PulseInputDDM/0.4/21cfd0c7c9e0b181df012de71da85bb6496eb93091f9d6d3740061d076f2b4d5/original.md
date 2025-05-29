```
load_neural_data(file::String; centered, dt, delay, pad, filtSD, extra_pad, cut, pcut)
```

Load neural data `.MAT` file and return an three `arrays`. The first `array` is the `data` formatted correctly for fitting the model. Each element of `data` is a module-defined class called `neuraldata`.

The package expects your data to live in a single `.MAT` file which should contain a struct called `rawdata`. Each element of `rawdata` should have data for one behavioral trial and `rawdata` should contain the following fields with the specified structure:

  * `rawdata.leftbups`: row-vector containing the relative timing, in seconds, of left clicks on an individual trial. 0 seconds is the start of the click stimulus
  * `rawdata.rightbups`: row-vector containing the relative timing in seconds (origin at 0 sec) of right clicks on an individual trial. 0 seconds is the start of the click stimulus.
  * `rawdata.T`: the duration of the trial, in seconds. The beginning of a trial is defined as the start of the click stimulus. The end of a trial is defined based on the behavioral event “cpoke_end”. This was the Hanks convention.
  * `rawdata.pokedR`: Bool representing the animal choice (1 = right).
  * `rawdata.spike_times`: cell array containing the spike times of each neuron on an individual trial. The cell array will be length of the number of neurons recorded on that trial. Each entry of the cell array is a column vector containing the relative timing of spikes, in seconds. Zero seconds is the start of the click stimulus. Spikes before and after the click inputs should also be included.

Arguments:

  * `file`: path to the file you want to load.

Optional arguments;

  * `break_sim_data`: this will break up simulatenously recorded neurons, as if they were recorded independently. Not often used by most users.
  * `centered`: Defaults to true. For the neural model, this aligns the center of the binned spikes, to the beginning of the binned clicks. This was done to fix a numerical problem. Most users will never need to adjust this.
  * `dt`: Binning of the spikes, in seconds.
  * `delay`: How much to offset the spikes, relative to the accumlator, in units of `dt`.
  * `pad`: How much extra time should spikes be considered before and after the begining of the clicks. Useful especially if delay is large.
  * `filtSD`: standard deviation of a Gaussin (in units of `dt`) to filter the spikes with to generate single trial firing rates (`μ_rnt`), and mean firing rate across all trials (`μ_t`).
  * `extra_pad`: Extra padding (in addition to `pad`) to add, for filtering purposes. In units of `dt`.
  * `cut`: How much extra to cut off at the beginning and end of filtered things (should be equal to `extra_pad` in most cases).
  * `pcut`: p-value for selecting cells.

Returns:

  * `data`: an `array` of length number of trials. Each element is a module-defined class called `neuraldata`.
  * `μ_rnt`: an `array` of length number of trials. Each entry of the sub-array is also an `array`, of length number of cells. Each entry of that array is the filtered single-trial firing rate of each neuron.
  * `μ_t`: an `array` of length number of cells. Each entry is the trial-averaged firing rate (across all trials).
