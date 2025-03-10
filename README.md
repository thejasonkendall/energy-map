# Energy Map with Graphviz

This repository contains a Graphviz DOT file for generating an "Energy Map" - a visual tool for prioritizing where to direct your energy and attention, as an alternative to traditional to-do lists.

## What is an Energy Map?

An Energy Map helps you visualize where your time, attention, and energy should be focused each day. Instead of tracking specific tasks, it keeps you aware of the important people and areas of life that deserve your energy.

## Quick Start

1. Install Graphviz on Debian/Ubuntu:
   ```bash
   sudo apt-get update
   sudo apt-get install graphviz
   ```

2. Generate the Energy Map image:
   ```bash
   dot -Tpng energy_map.dot -o energy_map.png
   ```

## The DOT File

```dot
digraph EnergyMap {
    // Graph settings
    graph [rankdir=TB, splines=true, overlap=false, nodesep=0.8, ranksep=1.0, fontname="Arial", label="Energy Map", labelloc=t, fontsize=20, bgcolor="transparent"];
    node [shape=circle, style=filled, fontname="Arial", fixedsize=true, width=1.2];
    edge [penwidth=2, arrowhead=none];

    // Main node
    Me [fillcolor="#6366F1", fontcolor=white, fontsize=15, width=1.5, label="Me"];

    // Category nodes
    Family [fillcolor="#EC4899", fontcolor=white, fontsize=14, label="Family"];
    Work [fillcolor="#F59E0B", fontcolor=white, fontsize=14, label="Work"];
    Friends [fillcolor="#10B981", fontcolor=white, fontsize=14, label="Friends"];
    Helping [fillcolor="#805AD5", fontcolor=white, fontsize=14, label="Helping"];

    // Personal nodes
    Health [fillcolor="#6366F1", fontcolor=white, fontsize=12, width=1.0, label="Health"];
    Hobbies [fillcolor="#6366F1", fontcolor=white, fontsize=12, width=1.0, label="Hobbies"];
    Finance [fillcolor="#6366F1", fontcolor=white, fontsize=12, width=1.0, label="Personal\nFinance"];
    ContentCreation [fillcolor="#6366F1", fontcolor=white, fontsize=12, width=1.0, label="Content\nCreation"];
    HamRadio [fillcolor="#6366F1", fontcolor=white, fontsize=10, width=0.8, label="Ham Radio"];

    // Work-related nodes
    PrimaryJob [fillcolor="#F59E0B", fontcolor=white, fontsize=12, width=1.1, label="Primary Job"];
    BigProject [fillcolor="#F59E0B", fontcolor=white, fontsize=12, width=1.0, label="Big Project 1"];
    Learning [fillcolor="#F59E0B", fontcolor=white, fontsize=12, width=1.0, label="Learning"];

    // Family node
    Home [fillcolor="#EC4899", fontcolor=white, fontsize=11, width=0.9, label="Home"];

    // Main connections from Me
    Me -> Family [color="#EC4899", penwidth=3];
    Me -> Work [color="#F59E0B", penwidth=3];
    Me -> Friends [color="#10B981", penwidth=3];
    Me -> Helping [color="#805AD5", penwidth=4];

    // Personal connections
    Me -> Health [color="#6366F1", penwidth=2];
    Me -> Hobbies [color="#6366F1", penwidth=2];
    Me -> Finance [color="#6366F1", penwidth=2];
    Me -> ContentCreation [color="#6366F1", penwidth=2];
    Me -> HamRadio [color="#6366F1", penwidth=2];
    Hobbies -> HamRadio [color="#6366F1", penwidth=1];

    // Work connections
    Work -> PrimaryJob [color="#F59E0B", penwidth=2];
    Work -> BigProject [color="#F59E0B", penwidth=2];
    Work -> Learning [color="#F59E0B", penwidth=2];

    // Family connection
    Family -> Home [color="#EC4899", penwidth=2];

    // Positioning hints to approximate layout
    {rank=same; Family; Me; Work}
    {rank=same; Helping; Friends}
    {rank=same; Health; Learning}
    {rank=same; Home; ContentCreation}
    {rank=same; Finance; Hobbies; PrimaryJob}
    {rank=min; Health; Learning}
    {rank=max; Friends; Helping; BigProject; HamRadio}
}
```

## Output Options

Generate different file formats:

```bash
# PNG image
dot -Tpng energy_map.dot -o energy_map.png

# SVG for web
dot -Tsvg energy_map.dot -o energy_map.svg

# PDF for printing
dot -Tpdf energy_map.dot -o energy_map.pdf
```

Adjust image size:
```bash
dot -Tpng -Gsize=8,6\! -Gdpi=300 energy_map.dot -o energy_map_large.png
```

## Customizing Your Energy Map

To modify the Energy Map:

1. Add/remove nodes by adding/removing their definitions and connections
2. Change colors by modifying the `fillcolor` attributes
3. Adjust node sizes with the `width` parameter
4. Reposition elements by modifying the `rank` statements

## Color Reference

| Area | Hex Color |
|------|-----------|
| Me   | #6366F1   |
| Family | #EC4899 |
| Work | #F59E0B |
| Friends | #10B981 |
| Helping | #805AD5 |

## Why Use an Energy Map?

- Focuses on high-level priorities rather than specific tasks
- Provides visual reminders of what deserves your attention
- Helps maintain balance across different life areas
- Prevents energy from being consumed by less important activities

## Further Customization

For more advanced styling, consider:

```bash
# Using neato for a more organic layout
neato -Tpng energy_map.dot -o energy_map_organic.png

# Using fdp for a force-directed layout
fdp -Tpng energy_map.dot -o energy_map_force.png
```