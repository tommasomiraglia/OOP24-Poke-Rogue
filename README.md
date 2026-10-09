# PokéRogue

A Java desktop roguelike inspired by [PokéRogue](https://pokerogue.net/), built as a team project for the Object-Oriented Programming course at the University of Bologna (2024/25).

**Authors:** Alex Casadio, Pietro Maretti, Tommaso Cosimo Miraglia, Egor Tverdohleb

## Game overview

- **Roguelike structure:** a run is a streak of battles against increasingly strong enemies, ending after 100 victories or at game over.
- **Team building:** before each run you pick three Pokémon from your box. The box grows as you catch new Pokémon and can be saved for future runs.
- **Turn-based battles** against wild Pokémon or trainers: use a move, throw a Poké Ball, switch Pokémon or run. Priority, type effectiveness, abilities, weather and status conditions are all handled.
- **Progression:** Pokémon gain experience, level up and learn new moves.
- **Shop:** after every battle, pick one of three free items or buy one of three paid ones.
- **Enemy AI** that chooses attacks and switch-ins based on the battle context.
- **Multiple saves** persisted as JSON.

## Architecture

The project follows the MVC pattern, with interfaces (`api` packages) separated from implementations (`impl` packages).

```
it.unibo.pokerogue
├── controller   Game loop, scenes, battle engine, enemy AI, effect interpreter
├── model        Pokémon, moves, abilities, items, trainers, factories, saving system
├── view         One view per scene (fight, shop, save, box, menu, ...)
└── utilities    Damage and effectiveness calculators, JSON reading, helpers
```

## Design highlights

- **Factory pattern** for Pokémon, moves, abilities and items.
- **Data-driven content:** moves, abilities and items are described in JSON, effects included. An `EffectInterpreter` based on Apache JEXL evaluates them at runtime, so new content needs no new Java code.
- **`DataExtractor`** that pulls species data from the [PokéAPI](https://pokeapi.co/) and stores it as local JSON.
- **Dynamic enemy generation** that scales with run progress.
- **Composable graphic system** (sprites, text, buttons, boxes, panels) that adapts to the screen size.
- Extensive use of `Optional`, lambdas and generics.

## Tech stack

Java, Gradle (Kotlin DSL), JUnit 5, Lombok, org.json, Apache Commons JEXL3, jOOL, SLF4J + Logback.

## My contribution

*Describe here the parts you worked on.*

## Documentation

The full project report (analysis, UML diagrams, development notes, user guide) is in [`report/report.pdf`](report/report.pdf), written in Italian.

## License

[MIT](LICENSE.txt)

*Non-commercial educational fan project. Pokémon and related names are trademarks of Nintendo, Creature Inc. and GAME FREAK inc.*
