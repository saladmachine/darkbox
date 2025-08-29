# DarkBox: Light-Free Growth Chamber System

**Academic research apparatus for controlled environment plant growth experiments using acetate metabolism instead of photosynthesis.**

## Project Overview

DarkBox is a specialized application of the WicdPico I&C platform designed for research into acetate-based plant growth. The system provides instrumentation and control for experiments conducted in complete darkness, where plants metabolize acetate instead of relying on photosynthesis.

## Critical Requirements

### Absolute Darkness
- **Zero light emission**: No power LEDs, status indicators, or any light sources
- **Light-tight sealing**: Complete chamber isolation from external light
- **Baffled ventilation**: Fan ducts designed to prevent light penetration
- **Dark room operation**: Windowless room with light-lock entry system
- **IR vision**: 940nm camera required for researcher navigation

### Research Context
- **Expensive reagents**: C13 tagged acetate requires bulletproof system validation
- **Academic timeline**: System must support HardwareX publication schedule
- **Controlled environment**: Precise temperature, humidity, CO2, and air circulation management

## Development Phases

### Phase 1: Petri Dish System
**Scope**: Plants growing in agar in petri dishes within dark chamber
- Single WicdPico node sufficient
- Environmental monitoring: CO2, temperature, humidity
- Light presence detection (safety/validation)
- Fan speed control for air circulation
- RTC timestamped data logging to SD card
- Web-based virtual control panel (VCP)

**Target**: System validation and proof of concept for Phase 2

### Phase 2: Hydroponic Integration  
**Scope**: Add hydroponic solution management to Phase 1 system
- **Solution reservoir**: Covered container with netcup lid and rockwool medium
- **Air stone bubbler**: Controlled oxygenation of nutrient solution
- **Level sensing**: Monitor solution volume
- **Fresh solution pumping**: Automated replenishment from external storage
- **Multi-device potential**: May require hub architecture for coordination

**Target**: Full production research system for C13 acetate experiments

## Technical Architecture

### Hardware Platform
- **Base**: WicdPico I&C system (Raspberry Pi Pico 2 W with CircuitPython)
- **Chamber**: 50cm cube light-tight enclosure
- **Sensors**: CO2 (SCD41), temperature/humidity (SHT45), light detection (BH1750)
- **Actuators**: Variable speed fan, solution pump, air stone bubbler
- **Data**: SD card logging with RTC timestamps

### Software Dependencies
- **Core Platform**: WicdPico foundation and module system (Git submodule)
- **Custom Modules**: DarkBox-specific instrumentation and control logic
- **Development**: VSCode integration with automated deployment scripts

### Repository Structure
```
darkbox/
├── wicdpico/                    # Git submodule to WicdPico platform
├── darkbox_modules/             # DarkBox-specific modules
│   ├── module_hydroponic.py     # Solution management (Phase 2)
│   ├── module_darkness.py       # Light monitoring and safety
│   └── module_chamber.py        # Environmental control
├── phase1/                      # Petri dish system configuration
│   └── code_phase1.py           # Phase 1 main application
├── phase2/                      # Hydroponic system configuration  
│   └── code_phase2.py           # Phase 2 main application
├── lib/                         # Symlinks to WicdPico modules
├── docs/                        # Research documentation
└── scripts/                     # Development and deployment tools
```

## Safety & Validation

### Pre-Research Testing
- **System integrity**: Complete darkness verification using light sensors
- **Environmental stability**: Temperature, humidity, CO2 control validation  
- **Solution management**: Pumping, level sensing, bubbler operation (Phase 2)
- **Data logging**: Continuous monitoring and backup systems
- **Remote monitoring**: VCP accessibility for experiment oversight

### Research Protection
- **No light contamination**: Multiple redundant darkness monitoring
- **Stable environment**: Automated control with manual override capability
- **Data backup**: Multiple logging systems to prevent data loss
- **Remote access**: Monitor experiments without physical chamber access

## Development Workflow

### VSCode Integration
- **Code templates**: `phase1/code_phase1.py` → `code.py` deployment
- **Automated sync**: Save triggers copy to both local git and CIRCUITPY drive
- **Serial monitoring**: Real-time system feedback during development
- **Module management**: Automatic copying of dependencies to Pico

### Dependency Management
- **WicdPico sync**: Controlled updates via Git submodule versioning
- **One-way dependency**: DarkBox uses WicdPico, no reverse dependencies
- **Version control**: Lock to specific WicdPico commits for stability

## Academic Context

### Publication Target
- **Journal**: HardwareX - open source scientific hardware
- **Timeline**: Support publication within 6 months
- **Focus**: Reproducible low-cost research instrumentation
- **Audience**: Academic researchers requiring specialized controlled environments

### Research Value
- **Novel growth method**: Darkbox system supports study of acetate metabolism instead of photosynthesis
- **Cost-effective platform**: Academic-grade instrumentation at maker prices
- **Reproducible design**: Open source hardware enabling research replication
- **Modular architecture**: Adaptable to other controlled environment applications

## License

MIT License

---

## Dependencies

This project depends on the WicdPico platform:
- **Repository**: https://github.com/saladmachine/wicdpico
- **Integration**: Git submodule for controlled dependency management
- **Documentation**: See WicdPico README for core platform capabilities

Built with CircuitPython and the Adafruit ecosystem for academic research applications.

AI Assistance Note: This project, including aspects of its code (e.g., structure, debugging assistance, error handling enhancements) and the drafting of this README.md, was significantly assisted by large language models, specifically Gemini by Google and Claude by Anthropic. This collaboration highlights the evolving landscape of modern open-source development, demonstrating how AI tools can empower makers to bring complex projects to fruition and achieve robust, production-ready implementations.
