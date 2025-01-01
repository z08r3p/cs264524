java c
EEET 3050 - Renewable Energy Systems 
Practical 1 - Characteristics of Doubly-fed Induction Generators (DFIG) 
Aim: The   aim   of   this   practical   is   to   evaluate   basic   operating   characteristics   of   a   Doubly-fed
induction   generator   directly   connected   to   a   grid   using   standard   MATLAB/SIMULINK   blocks given   in Simscape.
Objectives: Familiarise with the   block   diagram   of wind   generating   systems   given   in   Simscape.
Develop a simple   model   of a wind   power   plant directly   connected   to   a   grid
Simulation   of the   developed   model   and familiarise with   MATLAB   (2019a) Workspace   and graph   plottingBackground: In contrast to aconventional power generation, wind power is intermittent type. Thusthe   output power   of   a   wind   generator   cannot    be   controlled   on   demand. In   other   words, wind power is not dispatchable. The fluctuating output power of a wind generator   or   a wind farm   affects the voltage   profile,   losses,   reliability   and   stability   of   the   system.   The   output   power   of   a   wind   turbine   depends   on   wind   speed   which   is   stochastic   in   nature.   For   a   given   wind   speed,   the   turbine   efficiency   or   performance   coefficient   (Cp)   depends   on   turbine   speed   and   hence   tip-speed   ratio   (λ),   and   blade   pitch   angle   (β). The   turbine   power   Pm can   be   expressed   as:

Where,   ρ   is   the   air   density, A   is   the   blade   sweep   area   and   Vw is   the   wind   speed.In this   practical, a Doubly-fed-induction-generator      (DFIG) is used. To extract the   maximum   power   at   different   windspeeds, the   speed   of the   wind   turbine   and   hence   the generator is required to vary according to the wind speeds. This is done by   employing partial size back-to-back power electronic converters (ac-dc-ac). The converters   are   connected   to   a   common   dc   capacitor.   The   rotor   side   and   grid   side   converters   synthesize   an   ac voltage from   a   dc voltage   source   (represented   by the   dc   capacitor). The speed control range of the   DFIG depends on the size of the   converters   used. Usually   size   of   the   converter   is   about   30% of   rated   power   of   the   generator. Blade pitch angle of the wind turbine is also adjusted to limit the output   power   (at the   rated   value) during   higher windspeeds.
Description: Fig.1   illustrates   the   single   line   diagram   of   a   simple   wind   power   plant   connected   to   a   power   grid   and   supplying   a   local   load.   Fig.   2   illustrates   the   corresponding   Simulink   model   or   block   diagram. The   procedure   of   developing the   block   diagram   is   described   in the following.
Instructions: 
1.          Open   MATLAB   from   ‘Start’   menu.
2.          Select   ‘New’   →   ’Simulink   Model’   (or   type   ‘Simulink’   in   the   command   window)   to   get   a   new Simulink window.
3.          Click ‘Simulink Library’   icon  in the toolbar to get the window   of the   Simulink   library.
4.          The   DFIG   block   is   located   in   Simscape   →   Electrical   →   Specialised   Power   System   →   Renewables
→   Wind    →   Wind turbine doubly -   fed   Induction   Generator   (Phasor   type).
• Drag  drop the model on to the new file. 
• Save the file. 
5.            Type   ‘Powergui’   in   the   Simulink   library   search   space.   Drag      drop   the   ‘Powergui’   block   into   your   model.
6.          Search   for   the   following   blocks   and   drag      drop   them   into   your   Simulink   file.
•          Three-phase      source,   constant,   step,   scope,   clock,   Three-Phase   series   RLC   load,   Bus creator,   Bus selector, simout   block   (To workspace).
Hint:   Find   simout   block   (To   workspace)   in   ‘Sinks’ category.
7.          Connect   all   the   elements   as   shown   in   Fig.2.   Save   the   output   of   simout   block   as   ‘array’   instead of ‘timeseries’   .   (Hint: Change   the   ‘save   format’ option   of   simout   block)
8.          Right   click   the   ‘Bus   creator’   →   Block   parameter   →   Set   no.   of   inputs   to   ‘6’   .
9.          Right   click   on   the   ‘Bus   selector’    →   Block   parameter   →   Select   P   (pu),   Q   (pu),   Tm,   wr→   Click ‘OK’   .
10.   Choose   the   solver:   Click   on   the   ‘Variable   step   auto’   (bottom   right   corner)    →   Settings →   Solver   →   ode   45   (Dormand-Prince).
11.    Double   click   on   the   ‘Powergui’   block   →   Select   the   simulation   type   as   ‘Phasor’   and   Frequency as   ‘60Hz’   →   Click   ‘OK’   .
12.       Double   click   on   the   ‘Three-phase   Source’   and   enter   the   following   parameters:
•          Phase-to-phase   rms   voltage   -   575 V,   Frequency   -   60Hz,   Phase   angle   -   0,   3-phase   short circuit   level   -   100   MVA, X/R   ratio – 7, Base   voltage – 575 V
13.    Double   click   on   the   ‘Three-phase   load’   block   and   enter   the   following   parameters   :
•          In   the   ‘Parameters’   tab   →   Nominal   phase-to-phase   voltage   -   575   V,   configuration   -   Y代 写EEET 3050 - Renewable Energy Systems Practical 1 – Characteristics of Doubly-fed Induction GeneratorsMatlab
代做程序编程语言   (grounded),   frequency    -    60    Hz,    active      power      -          100    kW,    Inductive      and      capacitive reactive   power   -   0
•            In   the   ‘Load   flow’ tab   →   load   type   ‘Constant   Z’
14.    Double   click   on   the   ‘Constant’   block   connected   to   the   ‘Trip’   in   the   wind   turbine   model   →   set the   constant   to   ‘0’
15.    Double   click   on   the   ‘Step’   block   connected   to   the   ‘Wind’   in   the   wind   turbine   model   and   set   the following   parameters:
•       Step   time   -   5,   Initial   value   -   8,   Final   value   -   10
16.    Double   click   on the scope   and   click the   ‘Parameter’   icon  on the   toolbar   of the   scope   →   Select   the   ‘Logging’   tab → untick   the   box   for   ‘Limit   data   points   to   last’   →Click   ‘OK’   .   Do   this   change on   all the   scopes.
17.    Double   click   on   the   ‘Wind   Turbine’   model   and   enter   the   following   parameters:
•          Select      the ‘Generator’    option      →      Nominal      power,    line-to-line      voltage,    frequency      -   [1.5e6/0.9    575    60],   Stator      -      [    0.00706    0.171],    rotor      -    [    0.005    0.156],    Magnetizing inductance   -   2.9,   Inertia   constant,   friction   factor,   and   pairs   of   poles   -   [5.04   0.01   3],   Initial   conditions   -   [0.2 0   0   0   0   0]
•          Select   the   ‘Turbine’ option   →   Nominal   wind   turbine   mechanical   output   power   - 1.5e6,   Tracking   characteristic   speeds- [0.7 0.71 1.2 1.21],   Power   at   point   C   - 0.73,Wind   speed at   point   C   -   12,   Pitch   angle   controller   gain   - 500,   Maximum   pitch   angle   -   45,   Maximum rate   of   change   of   pitch   angle   -2
•          Click    on      the       ‘Display    wind      turbine      characteristics’      and      obtain      the      wind      turbine   characteristics.
• Save the figure. 
18.   Set   the   ‘Simulation   Stop   Time’   in   the   tool   bar   to ‘ 100‘ as   follows:

19.    Run   the   simulation   by   clicking   on   the   ‘Run’   icon   in   the   tool   bar.20.    Double   click   on   all   the   scopes   and   observe   the   parameter   variations. Click   the ‘Auto   scale’ icon  on the scope toolbar to view   the full   simulation.
Introduction to MATLAB Workspace: The MATLAB workspace consists of   the   variables   you create and store in memory during a MATLAB   session.   You   add   variables   to   the   workspace   by   using   functions, running   MATLAB   code, and   loading saved workspaces.

The Workspace   browser   displays the variables   in your   workspace.   From   the   Workspace   browser,   you can select variables to   view,   modify,   or   plot.
To open the Workspace   browser   if it   is   not currently   visible,   do   either   of   the   following:
•          Type workspace at the   Command   Window   prompt.
•          On   the   ‘Home’ tab   →   click   ‘Layout’. Then,   under   ‘Show’, select   ‘Workspace’   .
•          The   variables   you   selected   from   the   DFIG   in   the   previous   section   (P   (pu),   Q   (pu),   Tm   and wr) are   saved   in   the   ‘simout’   matrix.   (Hint: Click   ‘out’ to   see   ‘simout’   matrix)
Introduction to Plotting Data in MATLAB: 
MATLAB has an excellent set of graphic tools. Plotting a given data set or the results      of   computation   is   possible with very few commands. Since, all   your   data   related   to   the   simulation   is saved   in the   matrix   ‘simout’   in the Workspace, simply follow   the   following   steps   to   plot   different   graphs.
21.   Type      the   following   command   in   the   command   window   and   press   ‘Enter’:
• plot(out.simout( :,1),out.simout(:, 2)) 
The   x-axis   of   the   graph   denotes   the   time   variable   while   they-axis   represents   the   second   output   coming from the wind generator   model.
22.    In   order   to   add   labels   to   the   x-axis   andy-axis   and   a   title,   select   ‘Insert’   in   the   graph   and   select the   appropriate   labels   and   title. Then   type   the   label   names   and   the   title   as   illustrated   in   Fig. 4.

Fig. 4 Adding   axes   labels   and   titles   to   a   graphAlternatively,   Double   click   on   ‘arrow’   of figure toolbar   and   edit the   axis   by   double   clicking   on   any of the axis. Save the   plot or   use   ‘Copy   Figure’   option   from   Edit   menu   and   paste   the   figure   in the word   document.
23.   Similarly,   plot the following   outputs from the wind   generator   in   separate   figures   and   save   all   the figure files. Submit the graphs   in   a   report.
•          Time   vs   Active    power,   Time   vs   Reactive   power,   Time   vs   Wind   speed,   Time   vs   Rotor   speed, Time vs   Mechanical Torque
Report: The   report   should   include   a   brief   introduction,   all   plots   with   critical   analysis   and   discussion,   and   a   conclusion.   The      report   should      be   approximately   600   words   long,   excluding   figures,   diagrams,   and   tables.







         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
