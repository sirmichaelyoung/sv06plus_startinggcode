<h3>Sovol SV06 Plus Starting G-Code update for improved purging and bed leveling
</h3>

```
G90 ; use absoulte coordinates
M83 ; extruder relative mode

M104 S150 ; set nozzle temp to 150
G28 ; home all axes
;M420 S1 ;load mesh

M140 S[bed_temperature_initial_layer_single] ; set bed temp
M190 S[bed_temperature_initial_layer_single] ; wait for bed temp to stabilize
G29 ; Bed Mesh
G1 X0.1 Y10 Z5.0 F1500 ; move to start position
G1 Z0.26 F150 ; Move lower
M104 S[nozzle_temperature_initial_layer] ; set final extruder temp
M109 S[nozzle_temperature_initial_layer] ; wait for extruder temp

G4 S0.5 ; wait 0.5 seconds

G1 X0.1 Y150 Z0.3 F1500 E10 ; prime the nozzle
G1 X0.3 F1500
G1 X0.4 Y15 Z0.3 F1500 E15 ; prime the nozzle
G4 S0.1 ; wait 0.1 seconds

G1 Z0.6 F150 ; lift nozzle
G92 E0 ; Reset Extruder
G1 Z2 F150 ; lift nozzle more
```

This edit contains nozzle oozing to the purge zone, along with preheating the print bed prior to bed leveling for better consistency. This should be utilized for starting every print for optimal results. 

Minimizes first-layer errors, especially ideal for print farms and high-risk prints.
