# 65264931
Aesthetic study material import 'package:flame/components.dart';
import 'package:flame/input.dart';
import 'package:flutter/services.dart';
import 'bullet.dart';

class Player extends SpriteComponent with HasGameRef, KeyboardHandler {
  Player() : super(size: Vector2(50, 50));

  @override
  Future<void> onLoad() async {
    sprite = await gameRef.loadSprite('player.png'); // अपनी इमेज सेट करें
    position = gameRef.size / 2;
  }

  @override
  bool onKeyEvent(RawKeyEvent event, Set<LogicalKeyboardKey> keysPressed) {
    if (event is RawKeyDownEvent) {
      if (event.logicalKey == LogicalKeyboardKey.arrowLeft) {
        position.x -= 10;
      } else if (event.logicalKey == LogicalKeyboardKey.arrowRight) {
        position.x += 10;
      } else if (event.logicalKey == LogicalKeyboardKey.space) {
        gameRef.add(Bullet(position: position.clone()));
      }
    }
    return true;
  }

  
}
run
