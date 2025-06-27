# Faustina.github.io



import React, { useState } from 'react';
import { Card, CardContent, CardHeader, CardTitle } from '@/components/ui/card';
import { Input } from '@/components/ui/input';
import { Button } from '@/components/ui/button';
import { checkNumberSign, isPositive, isNegative } from '@/utils/numberChecker';

export const NumberChecker = () => {
  const [inputValue, setInputValue] = useState('');
  const [result, setResult] = useState<string | null>(null);

  const handleCheck = () => {
    const num = parseFloat(inputValue);
    
    if (isNaN(num)) {
      setResult('Please enter a valid number');
      return;
    }

    const sign = checkNumberSign(num);
    const details = `The number ${num} is ${sign}`;
    setResult(details);
  };

  const getResultColor = () => {
    if (!result || result.includes('Please enter')) return 'text-gray-600';
    if (result.includes('positive')) return 'text-green-600';
    if (result.includes('negative')) return 'text-red-600';
    return 'text-blue-600'; // for zero
  };

  return (
