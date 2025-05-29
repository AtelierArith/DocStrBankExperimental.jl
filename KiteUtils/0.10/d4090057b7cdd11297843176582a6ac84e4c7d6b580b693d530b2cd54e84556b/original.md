```
Settings
```

Flat struct, defining the settings of the Simulator and the Viewer.

  * `sim_settings::String`: name of the yaml file with the settings Default:
  * `log_file::String`: filename without extension  [replay only] Default:
  * `log_level::Float64`: how many messages to print on the console, 0=none Default: 2
  * `time_lapse::Float64`: relative replay speed Default: 0
  * `sim_time::Float64`: simulation time             [sim only] Default: 0
  * `segments::Int64`: number of tether segments Default: 0
  * `sample_freq::Int64`: sample frequency in Hz Default: 0
  * `zoom::Float64`: zoom factor for the system view Default: 0
  * `kite_scale::Float64`: relative zoom factor for the 4 point kite Default: 1.0
  * `fixed_font::String`: name or filepath+filename of alternative fixed pitch font Default:
  * `l_tether::Float64`: initial tether length       [m] Default: 0
  * `elevation::Float64`: initial elevation angle                [deg] Default: 0
  * `v_reel_out::Float64`: initial reel out speed    [m/s] Default: 0
  * `depower::Float64`: initial depower settings    [%] Default: 0
  * `abs_tol::Float64`: absolute tolerance of the DAE solver [m, m/s] Default: 0.0
  * `rel_tol::Float64`: relative tolerance of the DAE solver [-] Default: 0.0
  * `solver::String`: DAE solver, can be IDA or DFBDF Default: DFBDF
  * `linear_solver::String`: can be GMRES or Dense Default: GMRES
  * `max_order::Int64`: maximal order, usually between 3 and 5 Default: 4
  * `max_iter::Int64`: max number of iterations of the steady-state-solver Default: 1
  * `c0::Float64`: steering offset   -0.0032           [-] Default: 0
  * `c_s::Float64`: steering coefficient one point model Default: 0
  * `c2_cor::Float64`: correction factor one point model Default: 0
  * `k_ds::Float64`: influence of the depower angle on the steering sensitivity Default: 0
  * `delta_st::Float64`: steering increment (when pressing RIGHT) Default: 0
  * `max_steering::Float64`: max. steering angle of the side planes for four point model [degrees] Default: 0
  * `cs_4p::Float64`: correction factor for the steering sensitivity four point model Default: 1.0
  * `alpha_d_max::Float64`: max depower angle              [deg] Default: 0
  * `depower_offset::Float64`: at rel_depower=0.236 the kite is fully powered [%] Default: 23.6
  * `model::String`: file name of the 3D model of the kite for the viewer Default: data/kite.obj
  * `physical_model::String`: filename with or without extension for the foil shape [in dat format] Default:
  * `version::Int64`: version of the model to use Default: 1
  * `mass::Float64`: kite mass incl. sensor unit     [kg] Default: 0
  * `area::Float64`: projected kite area            [m^2] Default: 0
  * `rel_side_area::Float64`: relative side area               [%] Default: 0
  * `height_k::Float64`: height of the kite               [m] Default: 0
  * `alpha_cl::Vector{Float64}`: Default: []
  * `cl_list::Vector{Float64}`: Default: []
  * `alpha_cd::Vector{Float64}`: Default: []
  * `cd_list::Vector{Float64}`: Default: []
  * `cms::Float64`: steering dependant moment coefficient Default: 0
  * `width::Float64`: width of the kite                [m] Default: 0
  * `alpha_zero::Float64`: should be 5                      [degrees] Default: 0
  * `alpha_ztip::Float64`: Default: 0
  * `m_k::Float64`: relative nose distance; increasing m_k increases C2 of the turn-rate law Default: 0
  * `rel_nose_mass::Float64`: Default: 0
  * `rel_top_mass::Float64`: mass of the top particle relative to the sum of top and side particles Default: 0
  * `smc::Float64`:  steering moment coefficient Default: 0
  * `cmq::Float64`: pitch rate dependant moment coefficient Default: 0
  * `cord_length::Float64`: average aerodynamic cord length of the kite [m] Default: 0
  * `c_spring_kite::Float64`: unit spring constant coefficient of the kite springs [N] Default: 0
  * `damping_kite_springs::Float64`: unit damping coefficient of the kite springs [Ns] Default: 0
  * `rel_mass_p2::Float64`: relative mass of p2 Default: 0
  * `rel_mass_p3::Float64`: relative mass of p3 Default: 0
  * `rel_mass_p4::Float64`: relative mass of p4 and p5 Default: 0
  * `foil_file::String`: filename of the foil shape [in dat format] Default: data/ram*air*kite_foil.dat
  * `top_bridle_points::Vector{Vector{Float64}}`: top bridle points that are not on the kite body in CAD frame Default: [[0.290199, 0.784697, -2.61305], [0.392683, 0.785271, -2.61201], [0.498202, 0.786175, -2.62148], [0.535543, 0.786175, -2.62148]]
  * `bridle_tether_diameter::Float64`: bridle tether diameter [mm] Default: 2.0
  * `power_tether_diameter::Float64`: power tether diameter [mm] Default: 2.0
  * `steering_tether_diameter::Float64`: steering tether diameter [mm] Default: 1.0
  * `crease_frac::Float64`: distance along normalized foil chord for the trailing edge deformation crease Default: 0.82
  * `bridle_fracs::Vector{Float64}`: distances along normalized foil chord for bridle attachment points Default: [0.088, 0.31, 0.58, 0.93]
  * `fixed_index::Int64`: the bridle frac index around which the kite twists Default: 1
  * `quasi_static::Bool`: wether to use quasi-static tether points or not Default: false
  * `d_line::Float64`: bridle line diameter                  [mm] Default: 0
  * `h_bridle::Float64`: height of the bridle                    [m] Default: 0
  * `l_bridle::Float64`: sum of the lengths of the bridle lines [m] Default: 0
  * `rel_compr_stiffness::Float64`: relative compression stiffness of the kite springs Default: 0
  * `rel_damping::Float64`: relative damping of the kite spring (relative to main tether) Default: 0
  * `kcu_model::String`: model of the kite control unit, KCU1 or KCU2 Default: KCU1
  * `kcu_mass::Float64`: mass of the kite control unit   [kg] Default: 0
  * `kcu_diameter::Float64`: diameter of the kite control unit for drag calculation [m] Default: 0
  * `cd_kcu::Float64`: drag coefficient of the kite control unit Default: 0
  * `depower_zero::Float64`: depower setting for alpha_zero = 0 [%] Default: 0
  * `degrees_per_percent_power::Float64`: linear approximation [degrees/%] Default: 0
  * `power2steer_dist::Float64`: power to steering line distance  [m] Default: 0
  * `depower_drum_diameter::Float64`: Default: 0
  * `tape_thickness::Float64`: Default: 0
  * `v_depower::Float64`: max velocity of depowering in units per second (full range: 1 unit) Default: 0
  * `v_steering::Float64`: max velocity of steering in units per second   (full range: 2 units) Default: 0
  * `depower_gain::Float64`: 3.0 means: more than 33% error -> full speed Default: 3.0
  * `steering_gain::Float64`: Default: 3.0
  * `d_tether::Float64`: tether diameter                 [mm] Default: 0
  * `cd_tether::Float64`: drag coefficient of the tether Default: 0
  * `damping::Float64`: unit damping coefficient        [Ns] Default: 0
  * `c_spring::Float64`: unit spring constant coefficient [N] Default: 0
  * `rho_tether::Float64`: density of Dyneema                   [kg/m³] Default: 0
  * `e_tether::Float64`: axial tensile modulus of the tether     [Pa] Default: 0
  * `winch_model::String`: the winch model, either AsyncMachine or TorqueControlledMachine Default:
  * `max_force::Float64`: maximal (nominal) tether force; short overload allowed [N] Default: 4000
  * `v_ro_max::Float64`: maximal reel-out speed                      [m/s] Default: 8
  * `v_ro_min::Float64`: minimal reel-out speed (=max reel-in speed) [m/s] Default: -8
  * `max_acc::Float64`: maximal acceleration                       [m/s²] Default: 0
  * `drum_radius::Float64`: radius of the drum [m] Default: 0.1615
  * `gear_ratio::Float64`: ratio of the gear box Default: 6.2
  * `inertia_total::Float64`: inertia of the motor, gearbox and drum, as seen from the motor [kgm²] Default: 0
  * `f_coulomb::Float64`: coulomb friction [N] Default: 122.0
  * `c_vf::Float64`: coefficient for the viscous friction [Ns/m] Default: 30.6
  * `p_speed::Float64`: proportional gain for the speed controller Default: 0
  * `i_speed::Float64`: integral gain for the speed controller Default: 0
  * `v_wind::Float64`: wind speed at reference height          [m/s] Default: 0
  * `upwind_dir::Float64`: initial upwind direction                [deg] Default: 0
  * `temp_ref::Float64`: temperature at reference height         [°C] Default: 0
  * `height_gnd::Float64`: height of groundstation above see level  [m] Default: 0
  * `h_ref::Float64`:  reference height for the wind speed     [m] Default: 0
  * `rho_0::Float64`: air density at zero height and 15 °C    [kg/m³] Default: 0
  * `alpha::Float64`: exponent of the wind profile law Default: 0
  * `z0::Float64`: surface roughness                       [m] Default: 0
  * `profile_law::Int64`: 1=EXP, 2=LOG, 3=EXPLOG, 4=FAST*EXP, 5=FAST*LOG, 6=FAST_EXPLOG Default: 0
  * `use_turbulence::Float64`: turbulence intensity relative to Cabau, NL Default: 0
  * `v_wind_gnds::Vector{Float64}`: wind speeds at ref height for calculating the turbulent wind field [m/s] Default: []
  * `avg_height::Float64`: average height during reel out           [m] Default: 0
  * `rel_turbs::Vector{Float64}`: relative turbulence at the v*wind*gnds Default: []
  * `i_ref::Float64`: the expected value of the turbulence intensity at 15 m/s Default: 0
  * `v_ref::Float64`: five times the average wind speed in m/s at hub height over the full year    [m/s] Default: 0
  * `height_step::Float64`: grid resolution in z direction                                                 [m] Default: 0
  * `grid_step::Float64`: grid resolution in x and y direction                                           [m] Default: 0
