# Buildnaire release regression checklist

Before updating the public `index.html`, every release must pass this checklist.

## Static integrity
- JavaScript syntax check passes.
- Board contains exactly 24 squares with the formal map distribution.
- Skill master contains exactly 50 unique cards.
- Rarity distribution is N15 / R14 / S11 / L10.
- No card has a missing name or effect.
- Room code UI and server use the same format.

## Core gameplay
- Local game starts and closes the setup overlay.
- Dice rapid taps do not double-roll.
- MOVE/ACTION selection can only commit once.
- Movement completes without invalid positions.
- START, BANK, STATION and ARENA flows are checked.
- Mine, Shop, Casino and Battle arrival flows are checked.
- STATION warps to [13]–[17] and triggers the destination arrival effect.
- Card detail and owned-skill UI remain usable on desktop and mobile layouts.

## Full-game regression
- Complete 2-player CPU games to the normal 500G goal.
- Complete 4-player CPU games to the normal 500G goal.
- Verify winner, money, positions, skills and turn state remain valid.

## Online regression
- Host creates a 4-digit room.
- Guest joins with the same room code.
- Both clients show the same participant list.
- Lobby membership refreshes even if room.version is unchanged.
- Host can start after 2+ participants.
- Opponent-turn state refreshes if Realtime is missed.
- Leaving a room updates remaining players.

## Publish rule
Do not publish a game-code change until all applicable checks pass.
If any check fails, fix it and rerun the full applicable regression suite before deployment.
